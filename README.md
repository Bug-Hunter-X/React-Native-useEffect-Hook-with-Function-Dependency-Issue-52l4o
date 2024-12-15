# React Native useEffect Hook with Function Dependency Issue

This repository demonstrates a common, yet subtle, bug in React Native applications involving the `useEffect` hook and its dependency array.  The issue arises when a function is included in the dependency array, causing unexpected re-renders and potential performance problems.

The `bug.js` file contains the buggy code, showcasing the problem. The `bugSolution.js` file provides the corrected implementation.

## Problem
The issue stems from JavaScript's nature.  Each time the component re-renders, a *new* function object is created, leading to `useEffect` triggering on every render instead of only when relevant changes occur.

## Solution
The solution is to avoid including functions directly in the dependency array. Instead, we should either make the function a constant outside `useEffect` or use useCallback if we need the function to depend on props or state values. The example in `bugSolution.js` illustrates a fix using `useCallback`. 

## How to reproduce
1. Clone this repository.
2. Run `npm install` to install the dependencies.
3. Run `npx react-native run-android` (or `npx react-native run-ios`). 
4. Observe the console logs to see the unnecessary calls to `useEffect` in `bug.js`.  `bugSolution.js` will show the improvement after solving the issue.