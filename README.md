# Grade Calculator

A C++ console application that calculates a student's final letter grade
from a user-defined grading scheme and a set of assignment scores.

## Author
Clark Feenstra - COSC 1436, Spring 2026

## Description
[2-3 sentences describing what the program does and who it's for.]

## Features
- Time-of-day greeting
- User-defined grading scheme (Total Points + A/B/C/D cutoffs)
- Unlimited assignment entry with sentinel-controlled input
- Automatic sort of assignments highest to lowest
- Final letter grade and rounded percentage

## Files
| File          | Purpose                       |
|---------------|-------------------------------|
| main.cpp      | Driver program                |
| Greeting.h    | Greeting function declaration |
| Greeting.cpp  | Greeting function definition  |
| USER_GUIDE.md | End-user instructions         |

## How to Build
Using g++ (Linux / macOS / WSL / MinGW):

    g++ -std=c++17 main.cpp Greeting.cpp -o GradeCalculator

## How to Run
    ./GradeCalculator        # macOS / Linux
    GradeCalculator.exe      # Windows

## Requirements
- C++17 or newer compiler (g++, clang, or MSVC)

## Course Concepts Demonstrated
Chapters 1-12 of Fundamentals of C++ Programming by Richard L. Halterman.
