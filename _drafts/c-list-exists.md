---
layout: post_layout
title: 'C# List.Exists()'
date: 2019-05-27 11:40:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

Today, we are going to know a method which are Exists(). Exists() is used to determine whether the element is in the list or not, then return bool type to you. For example, if i want to find whether 5 is in \[1,2,3,4,5\] or not, we can use Exists() method.
```c-sharp
using System;
using System.Collections.Generic;

namespace ConsoleApp123
{
    class Program
    {
        static void Main(string[] args)
        {
            var arr = new List<int> {1, 2, 3, 4, 5}; //arr: [1,2,3,4,5]
            var result = arr.Exists(element => element == 5); //find whether 5 is arr or not
            Console.WriteLine(result); //true
        }
    }
}
```

```c-sharp
using System;
using System.Collections.Generic;

namespace ConsoleApp123
{
    class Program
    {
        static void Main(string[] args)
        {
            var arr = new List<int> {1, 2, 3, 4, 5};
            Console.WriteLine(IsExist(arr,5));
        }

        public static bool IsExist(List<int> arr, int num)
        {
            for (var i = 0; i < arr.Count; i++) //Traversing the list
            {
                if (arr[i] == num) //find whether num is in arr or not
                {
                    return true; //if yes return true
                }
            }

            return false; //return false
        }
    }
}
```
