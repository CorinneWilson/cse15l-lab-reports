# Lab Report 3

## Part 1: Bugs

Buggy Program (Before)

```
public class ArrayExamples {
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
}
```

Failure-Inducing Input
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  @Test
  public void testReversed2() {
    int[] input1 = {1, 2, 3};
    assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reversed(input1));
  }
}
```

Non Failure-Inucing Input
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```
Symptom

![Image](LR3_incorrect_ouput.png)
- As you can see, we are expecting the output of `{3, 2, 1}`. However, the actual output array we are getting has `0` as it's 0 index. In fact, the whole outputed array looks like `{0, 0, 0}`.

---

Buggy Program (After)
```
public class ArrayExamples {
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
}
```

---
The Fix
- In the Before code, we create a `newArray` with the same length as the input array, `arr`. When creating a new int array, all values in the array are set to 0. So `newArray` would look like `{0, 0, 0}`. Then, we set the forward iterating index elements of `arr` to the backward interating index elements of `newArray`. So `arr` at index 0 would be set to the value of `newArray` at index 2, etc. Thus, `arr` values at all it's indexes would be changed to 0. So, `arr` would look like `{0, 0, 0}` now too. We return `arr`, thus we return the array `{0, 0, 0}`.
- In the After code, we fix this by instead, setting the forward iterating index elements of `newArray` to the backward iterating index elements of `arr`. So `newArray` at index 0 would be set to the value of `arr` at index 2 (3), `newArray` at index 1 would be set to the value of `arr` at index 1 (2), etc. Thus, `newArray` would look like `{3, 2, 1}`. Therefore, instead of returning the original input array, `arr`, we now return the newly created reversed array, `newArray`.
 
Corrected Output
![Image](LR3_correct_output.png)

---

## Part 2: Researching Commands

`find -name`

This command can be useful when you don't remember where you saved a file, but do remember the exact name of the file you want to locate.

- We can use `-name` to find a file or directory within `./technical` with the String `preface.txt` in its name.
```
$ find . -name "*preface.txt"
./911report/preface.txt
```

 - We can use `-name` to find files or directories within `./technical` with the Strings `chapter-` followed sometime after by `.txt` (case-sensitive) in their names.
```
$ find . -name "*chapter-*.txt"
./911report/chapter-1.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
./911report/chapter-12.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-2.txt
./911report/chapter-3.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-8.txt
./911report/chapter-9.txt
```

Source: [https://www.redhat.com/sysadmin/linux-find-command](https://www.redhat.com/sysadmin/linux-find-command)

---

`find -iname`

This command can be useful when you don't remember where you saved a file, and don't remember the exact capitalization of the name of the file, but still remember it close enough to locate it. Or you can locate several files with a specific name in them, but one might be capitalized and the other might not.

- We can use `-iname` to find all files or directories within `./technical` with the String `report` (case-insensitive) in its name.
```
$ find . -iname "*report*"
./911report
./government/About_LSC/commission_report.txt
./government/About_LSC/Progress_report.txt
./government/About_LSC/reporting_system.txt
./government/About_LSC/Special_report_to_congress.txt
./government/About_LSC/State_Planning_Report.txt
./government/About_LSC/State_Planning_Special_Report.txt
./government/About_LSC/Strategic_report.txt
./government/Post_Rate_Comm/ReportToCongress2002WEB.txt
```

- We can use `-iname` to find all files or directories within `./technical/government` with the String `legal` (case-insensitive) in its name.
```
$ find ./government -iname "*legal*"
./government/About_LSC/LegalServCorp_v_VelazquezDissent.txt
./government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt
./government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
./government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
./government/Media/5_Legal_Groups.txt
./government/Media/Boone_legal_service.txt
./government/Media/Bridging_legal_aid_gap.txt
./government/Media/Coup_Reshapes_Legal_Aid.txt
./government/Media/Free_Legal_Assistance.txt
./government/Media/Free_legal_service.txt
./government/Media/Legal-aid_chief.txt
./government/Media/Legal_Aid_attorney.txt
./government/Media/Legal_Aid_campaign.txt
./government/Media/Legal_Aid_in_Clay_County.txt
./government/Media/Legal_Aid_looks_to_legislators.txt
./government/Media/Legal_Aid_Society.txt
./government/Media/Legal_hotline.txt
./government/Media/Legal_services_for_poor.txt
./government/Media/Legal_system_fails_poor.txt
./government/Media/less_legal_aid.txt
./government/Media/Marylands_Legal_Aid.txt
./government/Media/NJ_Legal_Services.txt
./government/Media/Paralegal_Honored.txt
./government/Media/Poor_Lacking_Legal_Aid.txt
./government/Media/Providing_Legal_Aid.txt
./government/Media/Supporting_Legal_Center.txt
./government/Media/Valley_Needing_Legal_Services.txt
```

Source: [https://www.redhat.com/sysadmin/linux-find-command](https://www.redhat.com/sysadmin/linux-find-command)

---

`find -type f`

This command can be useful when trying to find all elements within a directory (and its subdirectories) that are a file type.

- We can use `-type f` to find all files within `./technical`. This includes hundreds of files.
```
$ find . -type f 
./911report/chapter-1.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
./911report/chapter-12.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-2.txt
... More lines ...
./plos/pmed.0020281.txt
```

- We can use `-type f` to find all files only within the `./technical/911report` directory.
```
$ find ./911report -type f
./911report/chapter-1.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
./911report/chapter-12.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-2.txt
./911report/chapter-3.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-8.txt
./911report/chapter-9.txt
./911report/preface.txt
```

Source: [https://www.redhat.com/sysadmin/linux-find-command](https://www.redhat.com/sysadmin/linux-find-command)

---

`find -type d`

This command can be useful when trying to find all elements within a directory (and its subdirectories) that are a directory type.

- We can use `-type d` to find all directories/subdirectories within `./technical`.
```
$ find . -type d
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
./plos
```

- We can use `-type d` to find all directories/subdirectories within the `./technical/government` directory.
```
$ find ./government -type d
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
./government/Post_Rate_Comm
```

Source: [https://www.redhat.com/sysadmin/linux-find-command](https://www.redhat.com/sysadmin/linux-find-command)

---


