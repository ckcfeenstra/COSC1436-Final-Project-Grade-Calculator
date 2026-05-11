# Grade Calculator

## Introduction
   This program receives a student's grading scheme, takes the scores and the names of assignments, and performs calculations to show the student's final results.
   
## Getting Started
   In order to launch this program, the user must navigate to and click the [Code](https://studious-goldfish-7vq7p6wj9ggw3q57.github.dev/) button within the home page of the Github repository. This will redirect the user to Codespaces. Next, the user should click on the "Run and Debug" button located on the lefthand side menu. If the user has not done so already, he will be prompted to install the C/C++ Extension:

   ![C/C++ Extension image](/assets/packet.png "C/C++ Extension")
   
The necessary requirements to launch the program can be reviewed in the README.md file's "How to Build", "How to Run", and "Requirements" sections.
   

## Step-by-Step Walkthrough

   1. Once the program is running, the user will be prompted to enter a positive whole number for the total points possible in the course.
   
   2. The user will then be asked to input a positive decimal number such as 89.5 for the minimum number of points for each letter grade A-D. The grading scheme the user inputs will then be displayed.
   
   3. The program will then prompt the user to input the grade as a positive decimal number and then a new prompt will ask for the corresponding name of the assignment. This process will repeat until the user inputs a negative number in the prompt for the points earned for the assignment in order to terminate the repitition. The negative number is not included in the total sum.
   
   4. Once the prompts for assignments are terminated by a negative number input, the final results will be displayed for the user.


## Sample Session
   This is an example of successful compilation, inputs, and final results:
    
  ```
    
    Good Evening!

    Welcome to Your Grade Calculator!
    
    Grading Scheme Setup
    ====================
    Please input the Total Points Possible: 100
    Please input the Minimum Points for a 'A': 89.5
    Please input the Minimum Points for a 'B': 79.5
    Please input the Minimum Points for a 'C': 69.5
    Please input the Minimum Points for a 'D': 59.5
    
    The Grading Scheme You Input
    ============================
    Total Points Possible in the Course: 100
    Points needed for an 'A': 89.5
    Points needed for a 'B': 79.5
    Points needed for a 'C': 69.5
    Points needed for a 'D': 59.5
    
    Grade Calculation
    You will be prompted to input scores for all assignments.
    (Input a negative number to cease input and calculate letter grade.)
    
    Please input the points earned for Assignment 1: 10
    Please input the name for Assignment 1: Quiz 1
    Please input the points earned for Assignment 2: 10
    Please input the name for Assignment 2: Quiz 2
    Please input the points earned for Assignment 3: 9 
    Please input the name for Assignment 3: Quiz 3
    Please input the points earned for Assignment 4: 7 
    Please input the name for Assignment 4: Quiz 4
    Please input the points earned for Assignment 5: 9 
    Please input the name for Assignment 5: Quiz 5
    Please input the points earned for Assignment 6: 8
    Please input the name for Assignment 6: Quiz 6
    Please input the points earned for Assignment 7: 9
    Please input the name for Assignment 7: Quiz 7
    Please input the points earned for Assignment 8: 8
    Please input the name for Assignment 8: Quiz 8
    Please input the points earned for Assignment 9: 18.6
    Please input the name for Assignment 9: Exam
    Please input the points earned for Assignment 10: -1
    
    Assignments Sorted by Score (Highest to Lowest)
    ===============================================
    Exam: 18.6 points
    Quiz 1: 10 points
    Quiz 2: 10 points
    Quiz 3: 9 points
    Quiz 5: 9 points
    Quiz 7: 9 points
    Quiz 6: 8 points
    Quiz 8: 8 points
    Quiz 4: 7 points
    
    
    Final Results
    Total Points Earned: 88.6
    Total Points Possible: 100
    Total Percentage: 89%
    Final Letter Grade: B
    
  ```
   
## Understanding Your Results
   * Total Points Earned: The sum of all the points scored in the assignments.
   * Total Percentage: The Total Points Earned divided by the Total Points Possible, multiplied by 100, and rounded to the nearest whole number.
   * Final Letter Grade: Compares Total Points Earned with the user's grading scheme and outputs the appropriate letter grade.
   
## Troubleshooting
   If the program does not complete successfully,  here are a few common errors the user may have made:
     
     1. The user entered letters where numbers are supposed to be.
     
     2. The user forgot that, in order to terminate the prompts for assignments, he must enter a negative number.
    
     3. The user input a decimal number where a whole number belongs. 
