# Lab Report 4

## Step 4. Log into ieng6

`ssh <space> cowilson@ieng6.ucsd.edu <enter>`

- This runs the command `ssh cowilson@ieng6.ucsd.edu`. This allows me to remotely log into the ieng6 server.

## Step 5. Clone fork of repository from Github account (using SSH URL)

`git <space> clone <space> <ctrl+v> <enter>`

- In my clip board I had `git@github.com:CorinneWilson/lab7.git` copied. So, the keys `<crtl+v>` pasted it after `git clone`. Thus, I executed the command `git clone git@github.com:CorinneWilson/lab7.git` which clones my fork of the `lab7/` repository from my Github. 

## Step 6. Run the tests, demonstrating they fail

`cd <space> l <tab> <enter>`

- `cd` is used to change current working directory into the directory you give as an argument. Typing `l <tab>` autocompletes to `lab7/`. Thus, we are running the full command `cd lab7/` which changes the current working directory to `lab7/`.

`bash <space> t <tab> <enter>`

- `bash` is used to run a shell script. Typing `t <tab>` autocompletes to `tesh.sh` which includes the following commands to compile all files and run the tests:

```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```

- Thus, we are running the full command `bash test.sh`, which executes this script above and outputs the following failed results:

```
JUnit version 4.13.2
..E
Time: 0.517
There was 1 failure:
1) testMerge2(ListExamplesTests)
org.junit.runners.model.TestTimedOutException: test timed out after 500 milliseconds
        at ListExamples.merge(ListExamples.java:44)
        at ListExamplesTests.testMerge2(ListExamplesTests.java:19)

FAILURES!!!
Tests run: 2,  Failures: 1
```

## Step 7. Edit the code file to fix failing test

`vim <space> L <tab> . <tab> <enter>`

- `vim` is used to edit the particular file you give it as an argument. Typing `L <tab> . <tab>` autocompletes to `ListExamples.java`. Thus, we are running the full command `vim ListExamples.java` to now edit the `ListExamples.java` file.

`/index1 <enter> 9n e x i 2 <esc> :wq <enter>` 

- In vim `/index1` is used to find instances of the text `index1` which is what we are looking for. Then, `9n` goes to the ninth instance of `index1` which is the text that we want to alter. Next, `e` moves the cursor to the end of the word your currently at, so it moves to the 1 at the end of `index1`, and `x` removes the character at the cursor so now the word is `index` . Then, `i` changes the editor into insert mode and typing `2` inserts 2 at the spot of the cursor so now the word is `index2` which is what we wanted. `<esc>` ensures the editor goes back into normal mode and from there we type `:wq <enter>` so save and quit from vim.

## Step 8. Run the tests, demonstrating they now succeed
`<up> <up> <enter>`

- The `bash test.sh` command was 2 up in the search history so I used to up arrow twice two access it. Again `bash` runs the `test.sh` shell script which includes the following commands to compile and run the tests:

```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```

- Thus, we rerun the command `bash test.sh` now with a fixed implementation, which executes this script above and outputs the following correct results:

```
JUnit version 4.13.2
..
Time: 0.016

OK (2 tests)
```

## Step 9. Commit and push the resulting change to your Github account

`git <space> add L <tab> <enter>`

- `L <tab>` autocompletes to `ListExamples.java`. `git add` is used to add our changes in the given argument file to the staging area of our directory to use in the next commit. Thus, the full command we run is `git add ListExamples.java`, so we add our updated `ListExamples.java` to the staging area to get ready to commit and push it to my Github.

`git <space> commit <space> -m <space> "update <space> ListExamples.java" <enter>`

- `git commit -m` takes a snapshot of all the current states of the files in the staging area to save permanently to my Git directory, and create a timeline of the history of this repository/directory. After that `"update ListExamples.java"` is just the commit message to keep track of what happened/added to this commit.

`git <space> push <space> origin <space> main <enter>`

- This runs the command `git push origin main` which is used to upload the local repository we just updated back to the repository on my Github. `origin` means we push to the repository we got the orignal clone from and `main` is the main branch we push to.
