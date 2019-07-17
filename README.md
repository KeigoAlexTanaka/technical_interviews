# technical_interviews

https://leetcode.com/problems/reverse-integer/

Given a 32-bit signed integer, reverse digits of an integer.

Example 1:

Input: 123
Output: 321
Example 2:

Input: -123
Output: -321
Example 3:

Input: 120
Output: 21
Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

SOLUTION:

var reverse = function(x) {
    let num = x;
    if(x<0){
        num = x*-1;
    }
    let str = num +"";
    array=str.split("");
    if(x<0){
        array.push("-");
    }
    array=array.reverse();
    output=array.join("");
    if (output>2147483648 || output<-2147483647){
        return 0;
    }

    return output;
};

https://leetcode.com/problems/palindrome-number/
9. Palindrome Number
Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

Example 1:

Input: 121
Output: true
Example 2:

Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
Example 3:

Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
Follow up:

Coud you solve it without converting the integer to a string?

SOLUTION:

var isPalindrome = function(x) {
    if(x<0){
        return false;
    }
    let str = x+"";
    let arr = str.split("");
    let reverse = Array.from(arr).reverse();
    arr=arr.join("");
    reverse=reverse.join("");
    if (arr==reverse){
        return true;
    }
    return false;
};

https://leetcode.com/problems/roman-to-integer/

13. Roman to Integer

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

Example 1:

Input: "III"
Output: 3
Example 2:

Input: "IV"
Output: 4
Example 3:

Input: "IX"
Output: 9
Example 4:

Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
Example 5:

Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.

SOLUTION:

var romanToInt = function(s) {
    let counter=0;
    for (let i=s.length;i>=0;i--){
        if(s[i]=="I"){
            counter+=1;
            if(s[i+1]=="V" || s[i+1]=="X"){
                counter-=2;
            }
        }
        if(s[i]=="V"){
            counter+=5;
        }
        if(s[i]=="X"){
            counter+=10;
            if(s[i+1]=="L" || s[i+1]=="C"){
                counter-=20;
            }
        }
        if(s[i]=="L"){
            counter+=50;
        }
        if(s[i]=="C"){
            counter+=100;
            if(s[i+1]=="D" || s[i+1]=="M"){
                counter-=200;
            }
        }
        if(s[i]=="D"){
            counter+=500;
        }
        if(s[i]=="M"){
            counter+=1000;
        }
    }
    return counter;
};

https://leetcode.com/problems/longest-common-prefix/

14. Longest Common Prefix
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:

Input: ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
Note:

All given inputs are in lowercase letters a-z.

SOLUTION:

var longestCommonPrefix = function(strs) {
    if (strs === undefined || strs.length == 0) {
        return "";
    }
    let first = strs[0];
    for (let i =1;i<strs.length;i++){
        while(strs[i].indexOf(first)!=0){
            first = first.substring(0, first.length-1);
            console.log(first,strs[i].indexOf(first));
        }
    }
    return first;
};

https://leetcode.com/problems/valid-parentheses/

20. Valid Parentheses

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.

Example 1:

Input: "()"
Output: true
Example 2:

Input: "()[]{}"
Output: true
Example 3:

Input: "(]"
Output: false
Example 4:

Input: "([)]"
Output: false
Example 5:

Input: "{[]}"
Output: true

https://leetcode.com/problems/defanging-an-ip-address/

1108. Defanging an IP Address
Given a valid (IPv4) IP address, return a defanged version of that IP address.

A defanged IP address replaces every period "." with "[.]".

Example 1:

Input: address = "1.1.1.1"
Output: "1[.]1[.]1[.]1"
Example 2:

Input: address = "255.100.50.0"
Output: "255[.]100[.]50[.]0"
 

Constraints:

The given address is a valid IPv4 address.

SOLUTION:

var defangIPaddr = function(address) {
    return address = address.replace(/\./g, "[.]");
};

https://leetcode.com/problems/jewels-and-stones/

771. Jewels and Stones

You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

Example 1:

Input: J = "aA", S = "aAAbbbb"
Output: 3
Example 2:

Input: J = "z", S = "ZZ"
Output: 0
Note:

S and J will consist of letters and have length at most 50.
The characters in J are distinct.

var numJewelsInStones = function(J, S) {
    let counter=0;
    for (i in J){
        for (j in S){
            if (J[i]==S[j]){
                counter++;
            }
        }
    }
    return counter;
};