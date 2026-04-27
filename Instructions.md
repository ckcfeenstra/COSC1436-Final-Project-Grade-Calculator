# Assignment: Grade Calculator with Assignment Tracking and Sorting

## Overview

Starting from a basic grade calculator that computes cumulative scores, students will enhance the program to track individual assignment names alongside their scores using parallel vectors, then sort both vectors from highest to lowest score while maintaining the correspondence between assignment names and their scores.

## Learning Objectives

- Use two vectors in parallel: one for strings (assignment names) and one for floats (assignment scores)
- Store assignment names using `getline()` for proper string input handling
- Sort elements from both vectors from highest to lowest score while maintaining parallel structure
- Demonstrate proper vector manipulation and sorting techniques in C++

## Requirements

1. Add necessary `#include` statements for vector operations, string handling, and sorting algorithms
2. Declare two parallel vectors: one `std::vector<std::string>` for assignment names and one `std::vector<float>` for assignment scores
3. Modify the assignment input loop to collect both assignment names (using `getline()`) and scores, storing them in the parallel vectors
4. Implement sorting functionality to arrange both vectors from highest to lowest score while keeping names and scores paired correctly
5. Add output section to display the sorted assignment list with names and scores
6. Maintain all existing functionality (grading scheme setup, final grade calculation, percentage calculation)

## Getting Started

The starter code provides a complete grade calculator that:
- Displays a time-based greeting using a custom header file
- Collects grading scheme information (total points and grade thresholds)
- Uses a do-while loop to collect assignment scores and calculate a cumulative total
- Determines the final letter grade based on total points earned
- Calculates and displays the final percentage and grade

You will enhance this program to track individual assignments by name and display them in sorted order.

## Implementation Steps

### Add Required Headers and Vector Declarations

Add the necessary include statements at the top of `main.cpp` for vector operations, string handling, and sorting:

```cpp
#include <vector>
#include <string>
#include <algorithm>
```

Declare two parallel vectors after the existing variable declarations:

```cpp
std::vector<std::string> assignment_names;
std::vector<float> assignment_scores;
```

### Modify Assignment Input Loop to Collect Names and Scores

Replace the existing do-while loop that only collects scores. The new loop should:
- Prompt for and collect the assignment name using `getline()`
- Prompt for and collect the assignment score
- Store both in their respective parallel vectors
- Continue until a negative score is entered

```cpp
std::cin.ignore(); // Clear the input buffer before using getline()

do {
    std::string assignment_name;
    std::cout << "Please input the name for Assignment " << assignment << ": ";
    std::getline(std::cin, assignment_name);
    
    std::cout << "Please input the points earned for Assignment " << assignment << ": ";
    std::cin >> assignment_score;
    
    if (assignment_score >= 0) {
        assignment_names.push_back(assignment_name);
        assignment_scores.push_back(assignment_score);
        total_points_earned += assignment_score;
        assignment++;
        std::cin.ignore(); // Clear buffer after numeric input
    } else {
        score_input = false;
    }
} while (score_input);
```

The `std::cin.ignore()` calls are crucial for proper string input handling when mixing `getline()` with `>>` operators.

### Implement Parallel Vector Sorting

After the input loop but before the grade calculation, add code to sort both vectors from highest to lowest score while maintaining the parallel relationship:

```cpp
// Create a vector of indices for sorting
std::vector<int> indices(assignment_scores.size());
for (int i = 0; i < indices.size(); i++) {
    indices[i] = i;
}

// Sort indices based on scores in descending order
std::sort(indices.begin(), indices.end(), [&](int a, int b) {
    return assignment_scores[a] > assignment_scores[b];
});

// Create new sorted vectors
std::vector<std::string> sorted_names;
std::vector<float> sorted_scores;
for (int i : indices) {
    sorted_names.push_back(assignment_names[i]);
    sorted_scores.push_back(assignment_scores[i]);
}

// Replace original vectors with sorted versions
assignment_names = sorted_names;
assignment_scores = sorted_scores;
```

This approach uses an index-based sort to maintain the parallel relationship between names and scores.

### Add Sorted Assignment Display

Before the final results section, add code to display the sorted assignments:

```cpp
// Display sorted assignments
if (!assignment_names.empty()) {
    std::cout << "\nAssignments Sorted by Score (Highest to Lowest)\n";
    std::cout << "===============================================\n";
    for (size_t i = 0; i < assignment_names.size(); i++) {
        std::cout << assignment_names[i] << ": " << assignment_scores[i] << " points\n";
    }
    std::cout << std::endl;
}
```

This section only displays if assignments were actually entered, preventing empty output.

## Complete Program

Here is the complete enhanced `main.cpp` showing how all the pieces fit together:

```cpp
#include <iostream>
#include <cmath>
#include <ctime>
#include <vector>
#include <string>
#include <algorithm>
#include "Greeting.h"

int main() {
    // Variable declarations
    int total_course_points = 0;
    float A_points = 0.00;
    float B_points = 0.00;
    float C_points = 0.00;
    float D_points = 0.00;
    
    float total_points_earned = 0.00;
    float total_percentage_earned = 0.00;
    
    float assignment_score = 0.00;
    char earned_grade;
    bool score_input = true;
    int assignment = 1;

    // Parallel vectors for assignment tracking
    std::vector<std::string> assignment_names;
    std::vector<float> assignment_scores;

    // Display a time-based greeting
    displayGreeting();

    // Welcome message
    std::cout << "Welcome to Your Grade Calculator!" << std::endl;
    std::cout << std::endl;

    // Get grading scheme input
    std::cout << "Grading Scheme Setup" << std::endl;
    std::cout << "====================" << std::endl;

    std::cout << "Please input the Total Points Possible: ";
    std::cin >> total_course_points;

    // Use a for loop for grade inputs
    for (char grade = 'A'; grade <= 'D'; grade++) {
        std::cout << "Please input the Minimum Points for a '" << grade << "': ";
        if (grade == 'A') {
            std::cin >> A_points;
        } else if (grade == 'B') {
            std::cin >> B_points;
        } else if (grade == 'C') {
            std::cin >> C_points;
        } else if (grade == 'D') {
            std::cin >> D_points;
        }
    }

    // Display the grading scheme
    std::cout << std::endl;
    std::cout << "The Grading Scheme You Input" << std::endl;
    std::cout << "============================" << std::endl;
    std::cout << "Total Points Possible in the Course: " << total_course_points << std::endl;
    std::cout << "Points needed for an 'A': " << A_points << std::endl;
    std::cout << "Points needed for a 'B': " << B_points << std::endl;
    std::cout << "Points needed for a 'C': " << C_points << std::endl;
    std::cout << "Points needed for a 'D': " << D_points << std::endl;

    // Multiple Assignment Input using do-while
    std::cout << "\nGrade Calculation\n";
    std::cout << "You will be prompted to input scores for all assignments.\n";
    std::cout << "(Input a negative number to cease input and calculate letter grade.)\n\n";

    std::cin.ignore(); // Clear the input buffer before using getline()

    do {
        std::string assignment_name;
        std::cout << "Please input the name for Assignment " << assignment << ": ";
        std::getline(std::cin, assignment_name);
        
        std::cout << "Please input the points earned for Assignment " << assignment << ": ";
        std::cin >> assignment_score;
        
        if (assignment_score >= 0) {
            assignment_names.push_back(assignment_name);
            assignment_scores.push_back(assignment_score);
            total_points_earned += assignment_score;
            assignment++;
            std::cin.ignore(); // Clear buffer after numeric input
        } else {
            score_input = false;
        }
    } while (score_input);

    // Sort assignments by score (highest to lowest)
    if (!assignment_names.empty()) {
        // Create a vector of indices for sorting
        std::vector<int> indices(assignment_scores.size());
        for (int i = 0; i < indices.size(); i++) {
            indices[i] = i;
        }

        // Sort indices based on scores in descending order
        std::sort(indices.begin(), indices.end(), [&](int a, int b) {
            return assignment_scores[a] > assignment_scores[b];
        });

        // Create new sorted vectors
        std::vector<std::string> sorted_names;
        std::vector<float> sorted_scores;
        for (int i : indices) {
            sorted_names.push_back(assignment_names[i]);
            sorted_scores.push_back(assignment_scores[i]);
        }

        // Replace original vectors with sorted versions
        assignment_names = sorted_names;
        assignment_scores = sorted_scores;
    }

    // Determine the final grade
    if (total_points_earned >= A_points) {
        earned_grade = 'A';
    }
    else if (total_points_earned >= B_points) {
        earned_grade = 'B';
    }
    else if (total_points_earned >= C_points) {
        earned_grade = 'C';
    }
    else if (total_points_earned >= D_points) {
        earned_grade = 'D';
    }
    else {
        earned_grade = 'F';
    }

    // Calculate percentage and round it
    total_percentage_earned = (total_points_earned / total_course_points) * 100;
    total_percentage_earned = std::round(total_percentage_earned);

    // Display sorted assignments
    if (!assignment_names.empty()) {
        std::cout << "\nAssignments Sorted by Score (Highest to Lowest)\n";
        std::cout << "===============================================\n";
        for (size_t i = 0; i < assignment_names.size(); i++) {
            std::cout << assignment_names[i] << ": " << assignment_scores[i] << " points\n";
        }
        std::cout << std::endl;
    }

    // Display results
    std::cout << "\nFinal Results\n";
    std::cout << "Total Points Earned: " << total_points_earned << '\n';
    std::cout << "Total Points Possible: " << total_course_points << '\n';
    std::cout << "Total Percentage: " << total_percentage_earned << '%' << '\n';
    std::cout << "Final Letter Grade: " << earned_grade << '\n';

    return 0;
}
```

## Testing

To test your implementation:
1. Commit and push your changes to your repository
2. The autograder will run automatically and provide feedback
3. Check your repository on GitHub to see the test results
4. Green checkmarks indicate passing tests, red X's indicate failures
5. Click on the failed tests to see detailed error messages

## Grading Rubric

| Test Name | Points | Description |
|-----------|---------|-------------|
| `test_parallel_vectors_declaration` | 10 | Correctly declares parallel vectors for names and scores |
| `test_getline_usage` | 15 | Uses `getline()` to properly collect assignment names |
| `test_vector_population` | 20 | Correctly stores names and scores in parallel vectors |
| `test_sorting_functionality` | 25 | Implements sorting from highest to lowest score |
| `test_parallel_integrity` | 20 | Maintains correct pairing between names and scores after sorting |
| `test_sorted_output_display` | 10 | Displays sorted assignments with proper formatting |

**Total: 100 points**

## Tips and Hints

- **Buffer Management**: Always use `std::cin.ignore()` after numeric input when you plan to use `getline()` next. This prevents leftover newline characters from interfering with string input.

- **Parallel Vector Sorting**: The key challenge is sorting two vectors together. The index-based approach shown creates a vector of indices, sorts those indices based on the scores, then uses the sorted indices to rebuild both vectors in the correct order.

- **Lambda Functions**: The sorting uses a lambda function `[&](int a, int b) { return assignment_scores[a] > assignment_scores[b]; }`. The `[&]` captures all variables by reference, allowing access to `assignment_scores` within the lambda.

- **Vector Size Checking**: Always check if vectors are empty before trying to access or display their contents using `if (!assignment_names.empty())`.

- **Include Dependencies**: Remember to add `#include <vector>`, `#include <string>`, and `#include <algorithm>` at the top of your file for the new functionality.

- **Maintaining Existing Functionality**: The total points calculation should remain unchanged - you're still adding all scores to `total_points_earned` for the final grade calculation, just now also storing them individually for sorting and display.