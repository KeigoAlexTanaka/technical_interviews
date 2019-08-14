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

https://leetcode.com/problems/range-sum-of-bst/

938. Range Sum of BST
Given the root node of a binary search tree, return the sum of values of all nodes with value between L and R (inclusive).

The binary search tree is guaranteed to have unique values.

 

Example 1:

Input: root = [10,5,15,3,7,null,18], L = 7, R = 15
Output: 32
Example 2:

Input: root = [10,5,15,3,7,13,18,1,null,6], L = 6, R = 10
Output: 23
 

Note:

The number of nodes in the tree is at most 10000.
The final answer is guaranteed to be less than 2^31.

SOLUTION (DEPTH FIRST SEARCH):

var rangeSumBST = function(root, L, R) {
    let sum = 0;
    if(root == null) {
        return 0;
    }
    if(L <= root.val && root.val <= R) {
        sum = root.val;
    }
    if(L <= root.val || R <= root.val) {
       sum += rangeSumBST(root.left, L, R);
   } 
   if(root.val <= L || root.val <= R){
       sum += rangeSumBST(root.right, L, R);
   }
    return sum;
};

709. To Lower Case
Implement function ToLowerCase() that has a string parameter str, and returns the same string in lowercase.

 

Example 1:

Input: "Hello"
Output: "hello"
Example 2:

Input: "here"
Output: "here"
Example 3:

Input: "LOVELY"
Output: "lovely"

SOLUTION:

var toLowerCase = function(str) {
    return str.toLowerCase();
};

1021. Remove Outermost Parentheses

A valid parentheses string is either empty (""), "(" + A + ")", or A + B, where A and B are valid parentheses strings, and + represents string concatenation.  For example, "", "()", "(())()", and "(()(()))" are all valid parentheses strings.

A valid parentheses string S is primitive if it is nonempty, and there does not exist a way to split it into S = A+B, with A and B nonempty valid parentheses strings.

Given a valid parentheses string S, consider its primitive decomposition: S = P_1 + P_2 + ... + P_k, where P_i are primitive valid parentheses strings.

Return S after removing the outermost parentheses of every primitive string in the primitive decomposition of S.

 

Example 1:

Input: "(()())(())"
Output: "()()()"
Explanation: 
The input string is "(()())(())", with primitive decomposition "(()())" + "(())".
After removing outer parentheses of each part, this is "()()" + "()" = "()()()".
Example 2:

Input: "(()())(())(()(()))"
Output: "()()()()(())"
Explanation: 
The input string is "(()())(())(()(()))", with primitive decomposition "(()())" + "(())" + "(()(()))".
After removing outer parentheses of each part, this is "()()" + "()" + "()(())" = "()()()()(())".
Example 3:

Input: "()()"
Output: ""
Explanation: 
The input string is "()()", with primitive decomposition "()" + "()".
After removing outer parentheses of each part, this is "" + "" = "".
 

Note:

S.length <= 10000
S[i] is "(" or ")"
S is a valid parentheses string

804. Unique Morse Code Words
International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows: "a" maps to ".-", "b" maps to "-...", "c" maps to "-.-.", and so on.

For convenience, the full table for the 26 letters of the English alphabet is given below:

[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
Now, given a list of words, each word can be written as a concatenation of the Morse code of each letter. For example, "cba" can be written as "-.-..--...", (which is the concatenation "-.-." + "-..." + ".-"). We'll call such a concatenation, the transformation of a word.

Return the number of different transformations among all words we have.

Example:
Input: words = ["gin", "zen", "gig", "msg"]
Output: 2
Explanation: 
The transformation of each word is:
"gin" -> "--...-."
"zen" -> "--...-."
"gig" -> "--...--."
"msg" -> "--...--."

There are 2 different transformations, "--...-." and "--...--.".
Note:

The length of words will be at most 100.
Each words[i] will have length in range [1, 12].
words[i] will only consist of lowercase letters.

595. Big Countries

There is a table World

+-----------------+------------+------------+--------------+---------------+
| name            | continent  | area       | population   | gdp           |
+-----------------+------------+------------+--------------+---------------+
| Afghanistan     | Asia       | 652230     | 25500100     | 20343000      |
| Albania         | Europe     | 28748      | 2831741      | 12960000      |
| Algeria         | Africa     | 2381741    | 37100000     | 188681000     |
| Andorra         | Europe     | 468        | 78115        | 3712000       |
| Angola          | Africa     | 1246700    | 20609294     | 100990000     |
+-----------------+------------+------------+--------------+---------------+
A country is big if it has an area of bigger than 3 million square km or a population of more than 25 million.

Write a SQL solution to output big countries' name, population and area.

For example, according to the above table, we should output:

+--------------+-------------+--------------+
| name         | population  | area         |
+--------------+-------------+--------------+
| Afghanistan  | 25500100    | 652230       |
| Algeria      | 37100000    | 2381741      |
+--------------+-------------+--------------+

SOLUTION:

SELECT name, population, area from World WHERE (area>3000000 OR population>25000000)

https://leetcode.com/problems/flipping-an-image/

832. Flipping an Image

Given a binary matrix A, we want to flip the image horizontally, then invert it, and return the resulting image.

To flip an image horizontally means that each row of the image is reversed.  For example, flipping [1, 1, 0] horizontally results in [0, 1, 1].

To invert an image means that each 0 is replaced by 1, and each 1 is replaced by 0. For example, inverting [0, 1, 1] results in [1, 0, 0].

Example 1:

Input: [[1,1,0],[1,0,1],[0,0,0]]
Output: [[1,0,0],[0,1,0],[1,1,1]]
Explanation: First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]
Example 2:

Input: [[1,1,0,0],[1,0,0,1],[0,1,1,1],[1,0,1,0]]
Output: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
Explanation: First reverse each row: [[0,0,1,1],[1,0,0,1],[1,1,1,0],[0,1,0,1]].
Then invert the image: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
Notes:

1 <= A.length = A[0].length <= 20
0 <= A[i][j] <= 1

SOLUTION:

var flipAndInvertImage = function(A) {
  let output=[];
  let newArr=[];
  const reverseRow = (arr) => {
      arr.reverse();
  }
  A.map(reverseRow)
  for ( i in  A ) {
    newArr=[];
    for (j in A[i]) {
      if (A[i][j]==[0]){
        newArr.push(1)
      }
      if (A[i][j]==[1]){
        newArr.push(0);
      }
    }
    output.push(newArr);
  }
  return output;
};

https://leetcode.com/problems/sort-array-by-parity/

905. Sort Array By Parity

Given an array A of non-negative integers, return an array consisting of all the even elements of A, followed by all the odd elements of A.

You may return any answer array that satisfies this condition.

 

Example 1:

Input: [3,1,2,4]
Output: [2,4,3,1]
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.
 

Note:

1 <= A.length <= 5000
0 <= A[i] <= 5000

var sortArrayByParity = function(A) {
    let output = [];
    let even= [];
    let odd= [];
    for ( i in A ) {
        if (A[i]%2==0){
            even.push(A[i]);
        }
        if (A[i]%2==1){
            odd.push(A[i]);
        }
    }
    output = even.concat(odd);
    return output;
};

https://leetcode.com/problems/n-repeated-element-in-size-2n-array/

961. N-Repeated Element in Size 2N Array

In a array A of size 2N, there are N+1 unique elements, and exactly one of these elements is repeated N times.

Return the element repeated N times.

 

Example 1:

Input: [1,2,3,3]
Output: 3
Example 2:

Input: [2,1,2,5,3,2]
Output: 2
Example 3:

Input: [5,1,5,2,5,3,5,4]
Output: 5

SOLUTION:

var repeatedNTimes = function(A) {
    let B = A.sort();
    if (A[A.length/2+1]==A[A.length/2]){
        return A[A.length/2];
    }
    else{
        return A[A.length/2-1]
    }
};

https://leetcode.com/problems/squares-of-a-sorted-array/

977. Squares of a Sorted Array

Given an array of integers A sorted in non-decreasing order, return an array of the squares of each number, also in sorted non-decreasing order.

 

Example 1:

Input: [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Example 2:

Input: [-7,-3,2,3,11]
Output: [4,9,9,49,121]
 

Note:

1 <= A.length <= 10000
-10000 <= A[i] <= 10000
A is sorted in non-decreasing order.

var sortedSquares = function(A) {  
    let B = A.map((n)=>Math.pow(n,2));
    return B.sort(function(a, b){return a-b});
};

https://leetcode.com/problems/robot-return-to-origin/

657. Robot Return to Origin

There is a robot starting at position (0, 0), the origin, on a 2D plane. Given a sequence of its moves, judge if this robot ends up at (0, 0) after it completes its moves.

The move sequence is represented by a string, and the character moves[i] represents its ith move. Valid moves are R (right), L (left), U (up), and D (down). If the robot returns to the origin after it finishes all of its moves, return true. Otherwise, return false.

Note: The way that the robot is "facing" is irrelevant. "R" will always make the robot move to the right once, "L" will always make it move left, etc. Also, assume that the magnitude of the robot's movement is the same for each move.

Example 1:

Input: "UD"
Output: true 
Explanation: The robot moves up once, and then down once. All moves have the same magnitude, so it ended up at the origin where it started. Therefore, we return true.
 

Example 2:

Input: "LL"
Output: false
Explanation: The robot moves left twice. It ends up two "moves" to the left of the origin. We return false because it is not at the origin at the end of its moves.

SOLUTION:

var judgeCircle = function(moves) {
    let x = 0;
    let y = 0;
    for ( i in moves ) {
        if (moves[i] == "U"){
            y++;
        }
        if (moves[i] == "D"){
            y--;
        }
        if (moves[i] == "L"){
            x--;
        }
        if (moves[i] == "R"){
            x++;
        }
    }
    if (x==0&&y===0){
        return true;
        }
    else{
        return false;
    }
};

https://leetcode.com/problems/self-dividing-numbers/

728. Self Dividing Numbers

A self-dividing number is a number that is divisible by every digit it contains.

For example, 128 is a self-dividing number because 128 % 1 == 0, 128 % 2 == 0, and 128 % 8 == 0.

Also, a self-dividing number is not allowed to contain the digit zero.

Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.

Example 1:
Input: 
left = 1, right = 22
Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
Note:

The boundaries of each input argument are 1 <= left <= right <= 10000.

SOLUTION:

var selfDividingNumbers = function(left, right) {
    let output=[];
    let array = [];
    for (let i=left;i<=right;i++){
        array=(""+i).split("")
        if (array.every((n)=>i%n==0)) {
            output.push(i);
        }
    }
    return output;
};

SOLUTION: 

var diStringMatch = function(S) {
    let min = 0;
    let max = S.length;
    let output = [];
    for ( i in S ){
        if (S[i] == "I"){
            output.push(min);
            min++;
        }
        if (S[i] == "D"){
            output.push(max);
            max--;
        }
    }
    if (S[S.length-1]=="I"){
        output.push(max);
    }
    if (S[S.length-1]=="D"){
        output.push(min);
    }
    return output;
};

https://leetcode.com/problems/unique-email-addresses/

929. Unique Email Addresses

Every email consists of a local name and a domain name, separated by the @ sign.

For example, in alice@leetcode.com, alice is the local name, and leetcode.com is the domain name.

Besides lowercase letters, these emails may contain '.'s or '+'s.

If you add periods ('.') between some characters in the local name part of an email address, mail sent there will be forwarded to the same address without dots in the local name.  For example, "alice.z@leetcode.com" and "alicez@leetcode.com" forward to the same email address.  (Note that this rule does not apply for domain names.)

If you add a plus ('+') in the local name, everything after the first plus sign will be ignored. This allows certain emails to be filtered, for example m.y+name@email.com will be forwarded to my@email.com.  (Again, this rule does not apply for domain names.)

It is possible to use both of these rules at the same time.

Given a list of emails, we send one email to each address in the list.  How many different addresses actually receive mails? 

 

Example 1:

Input: ["test.email+alex@leetcode.com","test.e.mail+bob.cathy@leetcode.com","testemail+david@lee.tcode.com"]
Output: 2
Explanation: "testemail@leetcode.com" and "testemail@lee.tcode.com" actually receive mails
 

Note:

1 <= emails[i].length <= 100
1 <= emails.length <= 100
Each emails[i] contains exactly one '@' character.
All local and domain names are non-empty.
Local names do not start with a '+' character.

https://leetcode.com/problems/peak-index-in-a-mountain-array/

852. Peak Index in a Mountain Array

Let's call an array A a mountain if the following properties hold:

A.length >= 3
There exists some 0 < i < A.length - 1 such that A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1]
Given an array that is definitely a mountain, return any i such that A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1].

Example 1:

Input: [0,1,0]
Output: 1
Example 2:

Input: [0,2,1,0]
Output: 1
Note:

3 <= A.length <= 10000
0 <= A[i] <= 10^6
A is a mountain, as defined above.

SOLUTION:

var peakIndexInMountainArray = function(A) {
    let B = [];
    for (i in A){
        B.push(A[i]);
    }
    B.sort(function(a, b){return b - a})
    let max = B[0];
    return A.indexOf(max);
};

https://leetcode.com/problems/sort-array-by-parity-ii/

922. Sort Array By Parity II

Given an array A of non-negative integers, half of the integers in A are odd, and half of the integers are even.

Sort the array so that whenever A[i] is odd, i is odd; and whenever A[i] is even, i is even.

You may return any answer array that satisfies this condition.

 

Example 1:

Input: [4,2,5,7]
Output: [4,5,2,7]
Explanation: [4,7,2,5], [2,5,4,7], [2,7,4,5] would also have been accepted.

var sortArrayByParityII = function(A) {
    let output = [];
    let even = [];
    let odd = [];
    for ( i in A ) {
        if (A[i]%2==0){
            even.push(A[i]);
        }
        if (A[i]%2==1){
            odd.push(A[i]);
        }
    }
    for ( let i=0; i<A.length/2;i++) {
        output.push(even[i]);
        output.push(odd[i]);
    }
    return output;
};

509. Fibonacci Number
The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,

F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), for N > 1.
Given N, calculate F(N).

 

Example 1:

Input: 2
Output: 1
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.
Example 2:

Input: 3
Output: 2
Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.
Example 3:

Input: 4
Output: 3
Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.
 

Note:

0 ≤ N ≤ 30.

var fib = function(N) {
    if (N == 0) {
        return 0;
    }
    if (N == 1) {
        return 1;
    }
    return fib(N-1)+fib(N-2);
};


https://leetcode.com/problems/reveal-cards-in-increasing-order/

950. Reveal Cards In Increasing Order

In a deck of cards, every card has a unique integer.  You can order the deck in any order you want.

Initially, all the cards start face down (unrevealed) in one deck.

Now, you do the following steps repeatedly, until all cards are revealed:

Take the top card of the deck, reveal it, and take it out of the deck.
If there are still cards in the deck, put the next top card of the deck at the bottom of the deck.
If there are still unrevealed cards, go back to step 1.  Otherwise, stop.
Return an ordering of the deck that would reveal the cards in increasing order.

The first entry in the answer is considered to be the top of the deck.

 

Example 1:

Input: [17,13,11,2,3,5,7]
Output: [2,13,3,11,5,17,7]
Explanation: 
We get the deck in the order [17,13,11,2,3,5,7] (this order doesn't matter), and reorder it.
After reordering, the deck starts as [2,13,3,11,5,17,7], where 2 is the top of the deck.
We reveal 2, and move 13 to the bottom.  The deck is now [3,11,5,17,7,13].
We reveal 3, and move 11 to the bottom.  The deck is now [5,17,7,13,11].
We reveal 5, and move 17 to the bottom.  The deck is now [7,13,11,17].
We reveal 7, and move 13 to the bottom.  The deck is now [11,17,13].
We reveal 11, and move 17 to the bottom.  The deck is now [13,17].
We reveal 13, and move 17 to the bottom.  The deck is now [17].
We reveal 17.
Since all the cards revealed are in increasing order, the answer is correct.

SOLUTION IN PROGRESS:

var deckRevealedIncreasing = function(deck) {
    let sort = deck.sort(function(a, b){return a-b});
    let output = [];
    for ( let i=0; i<=(sort.length)/2; i++) {
        output.push(sort[i]);
        output.push(sort[i+sort.length/2]);
    }
    return output;
};

https://www.hackerrank.com/challenges/sock-merchant/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=warmup

Sock Merchant

function sockMerchant(n, ar) {
  let counts = {};
  let counter = 0;
  ar.forEach(function (x) { counts[x] = (counts[x] || 0) + 1; });
  
  Object.keys(counts).forEach(function (item) {
    counter+=Math.floor(counts[item]/2);
  })
  return counter;
  console.log(counter);
}