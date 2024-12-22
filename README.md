# Uncontrolled useEffect causing infinite render loop in React

This example demonstrates a common React error: an `useEffect` hook without a dependency array that causes an infinite render loop. The component continuously re-renders, leading to performance issues and potentially crashing the browser.

## Bug Description
The `useEffect` hook in `MyComponent` is intended to log the current `count` to the console after each render. However, because it lacks a dependency array (`[]`), it runs after *every* render, including the renders it triggers itself. This creates a feedback loop that never ends.

## Solution
The solution is to provide a dependency array to the `useEffect` hook.  This tells React to only run the effect when the specified dependencies change. In this case, the effect should only run when the `count` value changes.  Thus, we add `[count]` as the dependency array. Now the effect only runs when `count` is updated.

## How to reproduce
Clone this repository, then run `npm start` or `yarn start` to run the React application. Observe the console output which shows the component constantly rendering.  Then modify the `useEffect` function to include the dependency array to resolve this issue.  The console output will then demonstrate correct behaviour.
