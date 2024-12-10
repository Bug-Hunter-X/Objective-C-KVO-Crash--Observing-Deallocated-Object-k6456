# Objective-C KVO Crash: Observing a Deallocated Object

This repository demonstrates a common, yet subtle, bug in Objective-C related to Key-Value Observing (KVO).  The bug occurs when an observer continues to observe an object that has already been deallocated. This results in a crash or unpredictable behavior.

## The Problem

The `bug.m` file shows how adding an observer to an object and then releasing that object without removing the observer can lead to a crash. The observer will attempt to send messages to an object that no longer exists.

## The Solution

The `bugSolution.m` file provides a corrected version. The key change is the use of `removeObserver:forKeyPath:` in the `dealloc` method of the observed object.  This ensures that the observer is properly removed before the object is deallocated, preventing the crash.