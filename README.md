# 1813.-Sentence-Similarity
Daily Challenge | leetcode | 6 Oct 2025

You are given two strings sentence1 and sentence2, each representing a sentence composed of words. A sentence is a list of words that are separated by a single space with no leading or trailing spaces. Each word consists of only uppercase and lowercase English characters.

Two sentences s1 and s2 are considered similar if it is possible to insert an arbitrary sentence (possibly empty) inside one of these sentences such that the two sentences become equal. Note that the inserted sentence must be separated from existing words by spaces.

For example,

s1 = "Hello Jane" and s2 = "Hello my name is Jane" can be made equal by inserting "my name is" between "Hello" and "Jane" in s1.
s1 = "Frog cool" and s2 = "Frogs are cool" are not similar, since although there is a sentence "s are" inserted into s1, it is not separated from "Frog" by a space.
Given two sentences sentence1 and sentence2, return true if sentence1 and sentence2 are similar. Otherwise, return false.

 
class Solution {
    public boolean areSentencesSimilar(String sentence1, String sentence2) {
        //s1 = "hello Jane"
        //s2 = "Hello my name is Jane"
        String[] arr1 = sentence1.split(" "); //m
        String[] arr2 = sentence2.split(" "); //n

        int start = 0,
        end1 = arr1.length - 1,
        end2 = arr2.length - 1;

        if (arr1.length > arr2.length){
            return areSentencesSimilar(sentence2, sentence1);
        }

        //s1 = "Hello Jane"
        //s2 = "Hello my name is Jane"
        //arr1 = Hello,Jane
        //arr2 = Hello, my, name ,is, Jane
        while (start < arr1.length && arr1[start].equals(arr2[start])) {
            start = start + 1;
        }

        while (end1 >= 0 && arr1[end1].equals(arr2[end2])) {
            end1 = end1 - 1;
            end2 = end2 - 1;
        }

        return start > end1;

        //T: 0(m + n)
        //S: 0(m + n)

    }
}
