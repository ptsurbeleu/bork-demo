---
layout: post
title: Tips and hints
---
### Date/Time/Calendars
Leap year can be found out with the following helper function:

```
private bool IsLeap(int y) {
    return y % 4 == 0 && (y % 100 != 0 || y % 400 == 0);
}
```
List of months and how many days in each:

```
private int Feb(int yy) => IsLeap(yy) ? 29 : 28;

var months = new int[]{31,Feb(yy),31,30,31,30,31,31,30,31,30,31};
```
Date of `1971-01-01` was **Friday**, therefore `+4` in all calculations since **1971**:

```
private int DaysSince1971(string date) => (...) + 4;
```
How to avoid swapping smaller and larger dates/days:

```
Math.Abs(DaysSince1971(...) - DaysSince1971(...);

or

Math.Max(mm, nn) - Math.Min(mm, nn);
```
...
