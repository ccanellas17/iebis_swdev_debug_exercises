# iebis_swdev_debugging
Source code to test debugging

## Instructions
First, **Fork** this project.

There are three exercises splitted in three branches of this repository. You must switch branches to checkout the code of each exercise.
Then, find the bugs that appear in each branch.
Fix the bugs if you can and answer to the questions proposed below.
Commit the code before checking out a different branch to avoid loosing the fixes that you have made to the code.

Once that you are done fixing bugs, **to score you must**:
1. Switch to the master branch.
2. Type below in this README.md file the answer to each question and paste some code that you have used to solve them.
3. Commit the changes
4. Push to your GitHub repository
5. **Finally place a Pull Request so I can see your proposed answers**


## Exercises
### Exercise 1
In this code there is a class called WordAnalyzer that contains several methods that analyzes some characteristics of the word passed as argument when the object WordAnalyzer is created.

For some reason, the methods are not working properly, sometimes they return the correct value and others don't. You need to answer the next questions.

#### Why the method _firstMultipleCharacter_ is returning "c" for the word _comprehensive_, when the correct answer should be "e"?
>Because it was just returning the first letter that the code finds, therefore, we need to add +1 in the position to check if there is actually two consecutive letters together.

```
public char firstMultipleCharacter()
    {
        for (int i = 0; i < word.length(); i++)
        {
            char ch = word.charAt(i);
            if (find(ch, i) >= 0)
                return ch;
        }
        return 0;
    }

    private int find(char c, int pos)
    {
        for (int i = pos+1; i < word.length(); i++)
        {
            if (word.charAt(i) == c)
            {
                return i;
            }
        }
        return -1;
    }
```
#### Why the method _firstRepeatedCharacter_ is throwing an exception?
>Because we need to add an _else_ statement, because if not while the verification occurs, we go out of range. That's why we only need to change the range, n this case adding _word.length()-1;_

```
public char firstRepeatedCharacter() {
        for (int i = 0; i < word.length()-1; i++) {

            char ch = word.charAt(i);

                if (ch == word.charAt(i + 1)) {
                    return ch;
                }
            }

        return 0;
    }
```

#### Why the method _countGroupsRepeatedCharacters_ returns 3 in one case when it should be 4?

**Strategy**: Place breakpoints before the methods are executed, step into them and see what happens.


### Exercise 2
In this code we are placing mines in a board game where we have several spaces that can be mined. 
The boards can contain _Element_ objects, and since _Space_ and _Mine_ inherits from _Element_, the boards can contain this kind as well.

We have two boards of different size and place a different number of mines on each one. But in the second case it takes longer to place all the mines.

#### Why placing less bombs takes longer in the second case?
#### Knowing that usually there are going to be more bombs than spaces in the final boards, how would you change the method _minningTheBoard_ to be more efficient?

**Strategy**: Understand well what the code does. Use conditionals breakpoints.


### Exercise 3
In this case this code looks really simple. When the "d" reaches the value 1.0, the program should end, but it never does.

#### Why does not appear a message indicating that "d is 1"?
#### How will you fix it?
