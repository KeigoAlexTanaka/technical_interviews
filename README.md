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

