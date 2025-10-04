# LeetcodeQueSolution
🔹 1. First Unique Character in a String
🧩 Problem Statement:
Given a string s, find the first non-repeating character in it and return its index. If it doesn't exist, return -1.
🔍 Example:
Input: s = "leetcode"
Output: 0

Input: s = "loveleetcode"
Output: 2

Input: s = "aabb"
Output: -1
________________________________________
✅ Java Solution (with Explanation):
Java
public class FirstUniqueCharacter {
    public int firstUniqChar(String s) {
        int[] freq = new int[26]; // For storing frequency of each character

        // Step 1: Count frequency of each character
        for (char c : s.toCharArray()) {
            freq[c - 'a']++;
        }

        // Step 2: Find the first character with frequency 1
        for (int i = 0; i < s.length(); i++) {
            if (freq[s.charAt(i) - 'a'] == 1) {
                return i;
            }
        }

        return -1; // No unique character found
    }

    public static void main(String[] args) {
        FirstUniqueCharacter obj = new FirstUniqueCharacter();
        System.out.println(obj.firstUniqChar("leetcode"));       // Output: 0
        System.out.println(obj.firstUniqChar("loveleetcode"));   // Output: 2
        System.out.println(obj.firstUniqChar("aabb"));           // Output: -1
    }
}

Show more lines
🧠 Time & Space Complexity:
•	Time: O(n)
•	Space: O(1) — because the frequency array size is constant (26 letters)
________________________________________
🔹 2. First Letter to Appear Twice
🧩 Problem Statement:
Given a string s consisting of lowercase English letters, return the first letter that appears twice.
🔍 Example:
Input: s = "abccbaacz"
Output: "c"

Input: s = "abcdd"
Output: "d"
________________________________________
✅ Java Solution (with Explanation):
Java
public class FirstLetterToAppearTwice {
    public char repeatedCharacter(String s) {
        boolean[] seen = new boolean[26]; // To track seen characters

        for (char c : s.toCharArray()) {
            if (seen[c - 'a']) {
                return c; // First character that appears twice
            }
            seen[c - 'a'] = true;
        }

        return '\0'; // Should never reach here as per problem constraints
    }

    public static void main(String[] args) {
        FirstLetterToAppearTwice obj = new FirstLetterToAppearTwice();
        System.out.println(obj.repeatedCharacter("abccbaacz")); // Output: c
        System.out.println(obj.repeatedCharacter("abcdd"));     // Output: d
    }
}

Show more lines
🧠 Time & Space Complexity:
•	Time: O(n)
•	Space: O(1) — constant space for 26 letters
🔹 1. Counting Frequencies of Array Elements (GFG)
🧩 Problem:
Given an array of non-negative integers, count the frequency of each distinct element.
✅ Java Solution (Using HashMap):
Java
import java.util.HashMap;

public class FrequencyCounter {
    public static void countFrequencies(int[] arr) {
        HashMap<Integer, Integer> freqMap = new HashMap<>();

        for (int num : arr) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
        }

        for (int key : freqMap.keySet()) {
            System.out.println(key + " occurs " + freqMap.get(key) + " times");
        }
    }

    public static void main(String[] args) {
        int[] arr = {10, 20, 10, 5, 20};
        countFrequencies(arr);
    }
}

Show more lines
________________________________________
🔹 2. Sort Characters by Frequency (LeetCode 451)
🧩 Problem:
Given a string s, sort it in decreasing order based on the frequency of characters.
✅ Java Solution:
Java
import java.util.*;

public class FrequencySort {
    public String frequencySort(String s) {
        Map<Character, Integer> freqMap = new HashMap<>();

        for (char c : s.toCharArray()) {
            freqMap.put(c, freqMap.getOrDefault(c, 0) + 1);
        }

        PriorityQueue<Character> maxHeap = new PriorityQueue<>(
            (a, b) -> freqMap.get(b) - freqMap.get(a)
        );

        maxHeap.addAll(freqMap.keySet());

        StringBuilder sb = new StringBuilder();
        while (!maxHeap.isEmpty()) {
            char c = maxHeap.remove();
            sb.append(String.valueOf(c).repeat(freqMap.get(c)));
        }

        return sb.to Output: "eert" or "eetr"
    }
}

Show more lines
________________________________________
🔹 3. Two Sum (LeetCode 1)
🧩 Problem:
Find two indices such that their values add up to a given target.
✅ Java Solution:
Java
import java.util.*;

public class TwoSum {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }

        return new int[] {}; // No solution
    }

    public static void main(String[] args) {
        TwoSum ts = new TwoSum();
        int[] result = ts.twoSum(new int[]{2, 7, 11, 15}, 9);
        System.out.println(Arrays.toString(result)); // Output: [0, 1]
    }
}

Show more lines
________________________________________
🔹 4. Find a Pair with the Given Difference (GFG)
🧩 Problem:
Find if there exists a pair with a given absolute difference.
✅ Java Solution (Using HashSet):
Java
import java.util.*;

public class PairWithDifference {
    public static boolean hasPairWithDifference(int[] arr, int diff) {
        Set<Integer> set = new HashSet<>();

        for (int num : arr) {
            if (set.contains(num + diff) || set.contains(num - diff)) {
                return true;
            }
            set.add(num);
        }

        return false;
    }

    public static void main(String[] args) {
        int[] arr = {5, 20, 3, 2, 50, 80};
        int diff = 78;
        System.out.println(hasPairWithDifference(arr, diff)); // Output: true
    }
}

Show more lines
________________________________________
🔹 5. 3Sum (LeetCode 15)
🧩 Problem:
Find all unique triplets in the array which gives the sum of zero.
✅ Java Solution:
Java
import java.util.*;

public class ThreeSum {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();

        for (int i = 0; i < nums.length && nums[i] <= 0; i++) {
            if (i == 0 || nums[i] != nums[i - 1]) {
                int left = i + 1, right = nums.length - 1;
                while (left < right) {
                    int sum = nums[i] + nums[left] + nums[right];
                    if (sum < 0) left++;
                    else if (sum > 0) right--;
                    else {
                        result.add(Arrays.asList(nums[i], nums[left++], nums[right--]));
                        while (left < right && nums[left] == nums[left - 1]) left++;
                    }
                }
            }
        }

        return result;
    }
}

Show more lines
________________________________________
🔹 6. Intersection of Two Arrays (LeetCode 349)
🧩 Problem:
Return the intersection of two arrays (unique elements only).
✅ Java Solution:
Java
import java.util.*;

public class ArrayIntersection {
    public int intersection(int[] nums1, int[] nums2) {
        Set<Integer> set1 = new HashSet<>();
        for (int n : nums1) set1.add(n);

        Set<Integer> resultSet = new HashSet<>();
        for (int n : nums2) {
            if (set1.contains(n)) resultSet.add(n);
        }

        return resultSet.stream().mapToInt(i -> i).toArray();
    }
}

Show more lines
________________________________________
🔹 7. Intersection of Two Arrays II (LeetCode 350)
🧩 Problem:
Return the intersection of two arrays including duplicates.
✅ Java Solution:
Java
import java.util.*;

public class ArrayIntersectionII {
    public int[] intersect(int[] nums1, int[] nums2) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int n : nums1) map.put(n, map.getOrDefault(n, 0) + 1);

        List<Integer> result = new ArrayList<>();
        for (int n : nums2) {
            if (map.getOrDefault(n, 0) > 0) {
                result.add(n);
                map.put(n, map.get(n) - 1);
            }
        }

        return result.stream().mapToInt(i -> i).toArray();
    }
}


🔹 1. Longest Substring with At Most Two Distinct Characters (LeetCode 159)
✅ Java Solution:
Java
public class LongestTwoDistinct {
    public int lengthOfLongestSubstringTwoDistinct(String s) {
        int left = 0, maxLen = 0;
        Map<Character, Integer> map = new HashMap<>();

        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);
            map.put(c, map.getOrDefault(c, 0) + 1);

            while (map.size() > 2) {
                char leftChar = s.charAt(left);
                map.put(leftChar, map.get(leftChar) - 1);
                if (map.get(leftChar) == 0) map.remove(leftChar);
                left++;
            }

            maxLen = Math.max(maxLen, right - left + 1);
        }

        return maxLen;
    }
}

Show more lines
________________________________________
🔹 2. Longest Substring with At Most K Distinct Characters (LeetCode 340)
✅ Java Solution:
Java
public class LongestKDistinct {
    public int lengthOfLongestSubstringKDistinct(String s, int k) {
 map.getOrDefault(c, 0) + 1);

            while (map.size() > k) {
                char leftChar = s.charAt(left);
                map.put(leftChar, map.get(leftChar) - 1);
                if (map.get(leftChar) == 0) map.remove(leftChar);
                left++;
            }

            maxLen = Math.max(maxLen, right - left + 1);
        }

        return maxLen;
    }
}

Show more lines
________________________________________
🔹 3. Longest Repeating Character Replacement (LeetCode 424)
✅ Java Solution:
Java
public class LongestRepeatingChar {
    public int characterReplacement(String s, int k) {
        int[] count = new int[26];
        int maxCount = 0, left = 0, maxLen = 0;

        for (int right = 0; right < s.length(); right++) {
            count[s.charAt(right) - 'A']++;
            maxCount = Math.max(maxCount, count[s.charAt(right) - 'A']);

            while ((right - left + 1) - maxCount > k) {
                count[s.charAt(left) - 'A']--;
                left++;
            maxLen = Math.max(maxLen, right - left + 1);
        }

        return maxLen;
    }
}

Show more lines
________________________________________
🔹 4. Find if There is a Subarray with 0 Sum (GFG)
✅ Java Solution:
Java
public class ZeroSumSubarray {
    public static boolean hasZeroSumSubarray(int[] arr) {
        Set<Integer> set = new Hash            sum += num;
            if (sum == 0 || set.contains(sum)) return true;
            set.add(sum);
        }

        return false;
    }
}

________________________________________
🔹 5. Subarray Sum Equals K (LeetCode 560)
✅ Java Solution:
Java
public class SubarraySumEqualsK {
    public int subarraySum(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        int sum = 0, count = 0;

        for (int num : nums) {
            sum += num;
            count += map.getOrDefault(sum - k, 0);
            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }

        return count;
    }
}

Show more lines
________________________________________
🔹 6. Subarray Sums Divisible by K (LeetCode 974)
✅ Java Solution:
Java
public class SubarrayDivByK {
    public int subarraysDivByK(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        int sum = 0, count = 0;

        for (int num : nums) {
            sum += num;
            int mod = ((sum % k) + k) % k;
            count += map.getOrDefault(mod, 0);
            map.put(mod, map.getOrDefault(mod, 0) + 1);
        }

        return count;
    }
}

Show more lines
________________________________________
🔹 7. Valid Anagram (LeetCode 242)
✅ Java Solution:
Java
public class ValidAnagram {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;

        int[] count = new int[26];
        for (int i = 0; i < s.length(); i++) {
            count[s.charAt(i) - 'a']++;
            count[t.charAt(i) - 'a']--;
        }

        for (int c : count) {
            if (c != 0) return false;
        }

        return true;
    }
}

🔹 1. Group Anagrams (LeetCode 49)
🧩 Problem:
Group strings that are anagrams of each other.
✅ Java Solution:
Java
import java.util.*;

public class GroupAnagrams {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();

        for (String s : strs) {
            char[] chars = s.toCharArray();
            Arrays.sort(chars); // Sort characters to form the key
            String key = new String(chars);

            map.computeIfAbsent(key, k -> new ArrayList<>()).add(s);
        }

        return new ArrayList<>(map.values());
    }
}

Show more lines
________________________________________
🔹 2. Max Consecutive Ones (LeetCode 485)
🧩 Problem:
Find the maximum number of consecutive 1s in a binary array.
✅ Java Solution:
Java
public class MaxConsecutiveOnes {
    public int findMaxConsecutiveOnes(int[] nums) {
        int max = 0, count = 0;

        for (int num : nums) {
            if (num == 1) {
                count++;
                max = Math.max(max, count);
            } else {
                count = 0;
            }
        }

        return max;
    }
}

Show more lines
________________________________________
🔹 3. Max Consecutive Ones III (LeetCode 1004)
🧩 Problem:
Find the longest subarray with at most k zeros flipped to 1s.
✅ Java Solution:
Java
public class MaxConsecutiveOnesIII {
    public int longestOnes(int[] nums, int k) {
        int left = 0, right = 0;

        for (; right < nums.length; right++) {
            if (nums[right] == 0) k--;

            if (k < 0) {
                if (nums[left++] == 0) k++;
            }
        }

        return right - left;
    }
}

Show more lines
________________________________________
🔹 4. LRU Cache (LeetCode 146)
🧩 Problem:
Design a data structure that supports get and put in O(1) time using LRU policy.
✅ Java Solution (Using LinkedHashMap):
Java
import java.util.*;

class LRUCache extends LinkedHashMap<Integer, Integer> {
    private int capacity;

    public LRUCache(int capacity) {
        super(capacity, 0.75f, true); // accessOrder = true
        this.capacity = capacity;
    }

    public int get(int key) {
        return super.getOrDefault(key, -1);
    }

    public void put(int key, int value) {
        super.put(key, value);
    }

    @Override
    protected boolean removeEldestEntry(Map.Entry<Integer, Integer> eldest) {
        return size() > capacity;
    }
}

Show more lines
________________________________________
🔹 5. Sliding Window Maximum (LeetCode 239)
🧩 Problem:
Return the maximum value in each sliding window of size k.
✅ Java Solution (Using Deque):
Java
import java.util.*;

public class SlidingWindowMaximum {
    public int[] maxSlidingWindow(int[] nums, int k) {
        if (nums.length == 0) return new int[0];

        int[] result = new int[nums.length - k + 1];
        Deque<Integer> deque = new ArrayDeque<>();

        for (int i = 0; i < nums.length; i++) {
            // Remove indices out of window
            if (!deque.isEmpty() && deque.peek() < i - k + 1) {
                deque.poll();
            }

            smaller values from the back
            while (!deque.isEmpty() && nums[deque.peekLast()] < nums[i]) {
                deque.pollLast();
            }

            deque.offer(i);

            // Add to result
            if (i >= k - 1) {
                result[i - k + 1] = nums[deque.peek()];
            }
        }

        return result;
    }
}




🔹 Stack Data Structure (GFG)
A stack is a linear data structure that follows LIFO (Last In First Out). Think of it like a stack of plates — the last one placed is the first one removed.
Basic Operations:
•	push() – Add element to top
•	pop() – Remove top element
•	peek() – View top element
•	isEmpty() – Check if stack is empty
________________________________________
🔹 Valid Parentheses (LeetCode 20)
✅ Java Solution:
Java
public boolean isValid(String s) {
    Stack<Character> stack = new Stack<>();
    for (char c : s.toCharArray()) {
        if (c == '(') stack.push(')');
        else if (c == '{') stack.push('}');
        else if (c == '[') stack.push(']');
        else if (stack.isEmpty() || stack.pop() != c) return false;
    }
    return stack.isEmpty();
}

________________________________________
🔹 Remove All Adjacent Duplicates in String (LeetCode 1047)
✅ Java Solution:
Java
public String removeDuplicates(String s) {
    Stack<Character> stack = new Stack<>();
    for (char c : s.toCharArray()) {
        if (!stack.isEmpty() && stack.peek() == c) stack.pop();
        else stack.push(c);
    }

    StringBuilder sb = new StringBuilder();
    for (char c : stack) sb.append(c);
    return sb.toString();
}

________________________________________
🔹 Remove All Adjacent Duplicates in String II (LeetCode 1209)
✅ Java Solution:
Java
public String removeDuplicates(String s, int k) {
    Stack<Pair<Character, Integer>> stack = new Stack<>();

    for (char c : s.toCharArray()) {
        if (!stack.isEmpty() && stack.peek().getKey() == c) {
            stack.peek().setValue(stack.peek().getValue() + 1);
        } else {
            stack.push(new Pair<>(c, 1));
        }

        if (stack.peek().getValue() == k) stack.pop();
    }

    StringBuilder sb = new StringBuilder();
    for (Pair<Character, Integer> p : stack) {
        sb.append(String.valueOf(p.getKey()).repeat(p.getValue()));
    }

    return sb.toString();
}

Show more lines
________________________________________
🔹 Removing Stars From a String (LeetCode 2390)
✅ Java Solution:
Java
public String removeStars(String s) {
    Stack<Character> stack = new Stack<>();
    for (char c : s.toCharArray()) {
        if (c == '*') stack.pop();
        else stack.push(c);
    }

    StringBuilder sb = new StringBuilder();
    for (char c : stack) sb.append(c);
    return sb.toString();
}

________________________________________
🔹 Next Greater Element I (LeetCode 496)
✅ Java Solution:
Java
public int[] nextGreaterElement(int[] nums1, int[] nums2) {
    Map<Integer, Integer> map = new HashMap<>();
    Stack<Integer> stack = new Stack<>();

    for (int num : nums2) {
        while (!stack.isEmpty() && stack.peek() < num) {
            map.put(stack.pop(), num);
        }
        stack.push(num);
    }

    int[] result = new int[nums1.length];
    for (int i = 0; i < nums1.length; i++) {
        result[i] = map.getOrDefault(nums1[i], -1);
    }

    return result;
}

Show more lines
________________________________________
🔹 Daily Temperatures (LeetCode 739)
✅ Java Solution:
Java
public int[] dailyTemperatures(int[] temperatures) {
    int[] res = new int[temperatures.length];
    Stack<Integer> stack = new Stack<>();

    for (int i = 0; i < temperatures.length; i++) {
        while (!stack.isEmpty() && temperatures[i] > temperatures[stack.peek()]) {
            int prev = stack.pop();
            res[prev] = i - prev;
        }
        stack.push(i);
    }

    return res;
}

Show more lines
________________________________________
🔹 Trapping Rain Water (GFG)
✅ Java Solution (Two Pointers):
Java
public int trap(int[] height) {
    int left = 0, right = height.length - 1;
    int leftMax = 0, rightMax = 0, water = 0;

    while (left < right) {
        if (height[left] < height[right]) {
            if (height[left] >= leftMax) leftMax = height[left];
            else water += leftMax - height[left];
            left++;
        } else {
            if (height[right] >= rightMax) rightMax = height[right];
            else water += rightMax - height[right];
            right--;
        }
    }

    return water;
}

🔹 1. Kth Largest Element in an Array
Problem:
Return the k-th largest element in an unsorted array.
Java Solution (Min Heap):
Java
public int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    for (int num : nums) {
        minHeap.add(num);
        if (minHeap.size() > k) minHeap.poll();
    }
    return minHeap.peek();
}

________________________________________
🔹 2. Neither Minimum nor Maximum
Problem:
Return any number from the array that is neither the minimum nor the maximum.
Java Solution:
Java
public int findNonMinOrMax(int[] nums) {
    if (nums.length < 3) return -1;
    Arrays.sort(nums);
    return nums[1]; // Middle element after sorting
}

________________________________________
🔹 3. Sort Colors (Dutch National Flag)
Problem:
Sort an array of 0s, 1s, and 2s in-place.
Java Solution:
Java
public void sortColors(int[] nums) {
    int low = 0, mid = 0, high = nums.length - 1;
    while (mid <= high) {
        if (nums[mid] == 0) {
            swap(nums, low++, mid++);
        } else if (nums[mid] == 1) {
            mid++;
        } else {
            swap(nums, mid, high--);
        }
    }
}
private void swap(int[] nums, int i, int j) {
    int temp = nums[i]; nums[i] = nums[j]; nums[j] = temp;
}

Show more lines
________________________________________
🔹 4. Missing Number
Problem:
Find the missing number from 0 to n.
Java Solution (XOR):
Java
public int missingNumber(int[] nums) {
    int xor = nums.length;
    for (int i = 0; i < nums.length; i++) {
        xor ^= i ^ nums[i];
    }
    return xor;
}

________________________________________
🔹 5. Maximum Product of Three Numbers
Problem:
Find the maximum product of any three numbers.
Java Solution:
Java
public int maximumProduct(int[] nums) {
    Arrays.sort(nums);
    int n = nums.length;
    return Math.max(nums[n-1] * nums[n-2] * nums[n-3],
                    nums[0] * nums[1] * nums[n-1]);
}

________________________________________
🔹 6. Remove Duplicates from Sorted Array
Problem:
Remove duplicates in-place and return the new length.
Java Solution:
Java
public int removeDuplicates(int[] nums) {
    int i = 0;
    for (int n : nums) {
        if (i == 0 || n != nums[i - 1]) {
            nums[i++] = n;
        }
    }
    return i;
}

________________________________________
🔹 7. Left Rotate the Array by One
Java Solution:
Java
public void rotateLeftByOne(int[] arr) {
    int temp = arr[0];
    for (int i = 1; i < arr.length; i++) {
        arr[i - 1] = arr[i];
    arr[arr.length - 1] = temp;
}

________________________________________
🔹 8. Rotate Array
Problem:
Rotate the array to the right by k steps.
Java Solution (Reversal):
Java
public void rotate(int[] nums, int k) {
    k %= nums.length;
    reverse(nums, 0, nums.length - 1);
    reverse(nums, 0, k - 1);
    reverse(nums, k, nums.length - 1);
}
private void reverse(int[] nums, int start, int end) {
    while (start < end) {
        int temp = nums[start];
        nums[start++] = nums[end];
        nums[end--] = temp;
    }
}

________________________________________
🔹 9. Move Zeroes
Problem:
Move all 0s to the end while maintaining the order of non-zero elements.
Java Solution:
Java
public void moveZeroes(int[] nums) {
    int index = 0;
    for (int num : nums) {
        if (num != 0) nums[index++] = num;
    }
    while (index < nums.length) nums[index++] = 0;
}

________________________________________
🔹 10. Max Consecutive Ones
Problem:
Find the maximum number of consecutive 1s.
Java Solution:
Java
public int findMaxConsecutiveOnes(int[] nums) {
    int max = 0, count = 0;
    for (int num : nums) {
        if (num == 1) {
            count++;
            max = Math.max(max, count);
        } else {
            count = 0;
        }
    }
    return max;
}

🔹 1. Valid Anagram
🧩 Problem:
Check if two strings are anagrams of each other (same characters, same frequency).
✅ Java Solution:
Java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) return false;

    int[] count = new int[26];
    for (int i = 0; i < s.length(); i++) {
        count[s.charAt(i) - 'a']++;
        count[t.charAt(i) - 'a']--;
    }

    for (int c : count) {
        if (c != 0) return false;
    }

    return true;
}

Show more lines
________________________________________
🔹 2. Reverse String
🧩 Problem:
Reverse the characters of a string in-place.
✅ Java Solution:
Java
public void reverseString(char[] s) {
    int left = 0, right = s.length - 1;
    while (left < right) {
        char temp = s[left];
        s[left++] = s[right];
        s[right--] = temp;
    }
}

________________________________________
🔹 3. Reverse Words in a String
🧩 Problem:
Reverse the order of words in a string. Words are separated by spaces.
✅ Java Solution:
Java
public String reverseWords(String s) {
    String[] words = s.trim().split("\\s+");
    Collections.reverse(Arrays.asList(words));
    return String.join(" ", words);
}

________________________________________
🔹 4. Valid Palindrome
🧩 Problem:
Check if a string is a palindrome, considering only alphanumeric characters and ignoring cases.
✅ Java Solution:
Java
public boolean isPalindrome(String s) {
    int left = 0, right = s.length() - 1;
    while (left < right) {
        while (left < right && !Character.isLetterOrDigit(s.charAt(left))) left++;
        while (left < right && !Character.isLetterOrDigit(s.charAt(right))) right--;
        if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) return false;
        left++;
        right--;
    }
    return true;
}

________________________________________
🔹 5. Valid Palindrome II
🧩 Problem:
Return true if the string can be a palindrome after deleting at most one character.
✅ Java Solution:
Java
public boolean validPalindrome(String s) {
    int left = 0, right = s.length() - 1;
    while (left < right) {
        if (s.charAt(left) != s.charAt(right)) {
            return isPalindrome(s, left + 1, right) || isPalindrome(s, left, right - 1);
        }
        left++;
        right--;
    }
    return true;
}

private boolean isPalindrome(String s, int left, int right) {
    while (left < right) {
        if (s.charAt(left++) != s.charAt(right--)) return false;
    }
    return true;
}

Show more lines
________________________________________
🔹 6. Consecutive Characters
🧩 Problem:
Return the maximum number of consecutive repeating characters in the string.
✅ Java Solution:
Java
public int maxPower(String s) {
    int max = 1, count = 1;
    for (int i = 1; i < s.length(); i++) {
        if (s.charAt(i) == s.charAt(i - 1)) {
            count++;
            max = Math.max(max, count);
        } else {
            count = 1;
        }
    }
    return max;
}

________________________________________
🔹 7. Longest Common Prefix
🧩 Problem:
Find the longest common prefix string among an array of strings.
✅ Java Solution:
Java
public String longestCommonPrefix(String[] strs) {
    if (strs == null || strs.length == 0) return "";

    String prefix = strs[0];
    for (int i = 1; i < strs.length; i++) {
        while (strs[i].indexOf(prefix) != 0) {
            prefix = prefix.substring(0, prefix.length() - 1);
            if (prefix.isEmpty()) return "";
        }
    }
    return prefix;
}

🔹 1. Search an Element in a Linked List (GFG)
Problem:
Given the head of a linked list and a key, determine whether the key exists in the list.
✅ Iterative Java Solution:
Java
public boolean searchIterative(Node head, int key) {
    Node current = head;
    while (current != null) {
        if (current.data == key) return true;
        current = current.next;
    }
    return false;
}

✅ Recursive Java Solution:
Java
public boolean searchRecursive(Node head, int key) {
    if (head == null) return false;
    if (head.data == key) return true;
    return searchRecursive(head.next, key);
}

________________________________________
🔹 2. Find Length of a Linked List (GFG)
Problem:
Find the number of nodes in a singly linked list.
✅ Iterative Java Solution:
Java
public int getLengthIterative(Node head) {
    int count = 0;
    Node current = head;
    while (current != null) {
        count++;
        current = current.next;
    }
    return count;
}

✅ Recursive Java Solution:
Java
public int getLengthRecursive(Node head) {
    if (head == null) return 0;
    return 1 + getLengthRecursive(head.next);
}

________________________________________
🔹 3. Middle of the Linked List (LeetCode 876)
Problem:
Return the middle node of a singly linked list. If there are two middle nodes, return the second one.
✅ Java Solution:
Java
public ListNode middleNode(ListNode head) {
    ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
}

________________________________________
🔹 4. Delete the Middle Node of a Linked List (LeetCode 2095)
Problem:
Delete the middle node of a linked list and return the head of the modified list.
✅ Java Solution:
Java
public ListNode deleteMiddle(ListNode head) {
    if (head == null || head.next == null) return null;

    ListNode slow = head, fast = head, prev = null;
    while (fast != null && fast.next != null) {
        prev = slow;
        slow = slow.next;
        fast = fast.next.next;
    }
    prev.next = slow.next;
    return head;
}

________________________________________
🔹 5. Merge Two Sorted Lists (LeetCode 21)
Problem:
Merge two sorted linked lists into one sorted list.
✅ Java Solution:
Java
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(0);
    ListNode current = dummy;

    while (l1 != null && l2 != null) {
        if (l1.val <= l2.val) {
            current.next = l1;
            l1 = l            current.next = l2;
            l2 = l2.next;
        }
        current = current.next;
    }

    current.next = (l1 != null) ? l1 : l2;
    return dummy.next;
}

Show more lines
________________________________________
🔹 6. Palindrome Linked List (LeetCode 234)
Problem:
Check if a linked list is a palindrome.
✅ Java Solution:
Java
public boolean isPalindrome(ListNode head) ListNode slow = head, fast = head;
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }

    ListNode secondHalf = reverse(slow);
    ListNode firstHalf = head;

    while (secondHalf != null) {
        if (firstHalf.val != secondHalf.val) return false;
        firstHalf = firstHalf.next;
        secondHalf = secondHalf.next;
    }

import java.util.*;

public class AllSolutions {

    // 1. Counting Frequencies of Array Elements
    public static void countFrequencies(int[] arr) {
        HashMap<Integer, Integer> freqMap = new HashMap<>();
        for (int num : arr) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
        }
        for (int key : freqMap.keySet()) {
            System.out.println(key + " occurs " + freqMap.get(key) + " times");
        }
    }

    // 2. Sort Characters by Frequency
    public static String frequencySort(String s) {
        Map<Character, Integer> freqMap = new HashMap<>();
        for (char c : s.toCharArray()) {
            freqMap.put(c, freqMap.getOrDefault(c, 0) + 1);
        }
        PriorityQueue<Character> maxHeap = new PriorityQueue<>((a, b) -> freqMap.get(b) - freqMap.get(a));
        maxHeap.addAll(freqMap.keySet());
        StringBuilder sb = new StringBuilder();
        while (!maxHeap.isEmpty()) {
            char c = maxHeap.remove();
            sb.append(String.valueOf(c).repeat(freqMap.get(c)));
        }
        return sb.toString();
    }

    // 3. Two Sum
    public static int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int comp = target - nums[i];
            if (map.containsKey(comp)) {
                return new int[]{map.get(comp), i};
            }
            map.put(nums[i], i);
        }
        return new int[]{};
    }

    // 4. Find a Pair with the Given Difference
    public static boolean hasPairWithDifference(int[] arr, int diff) {
        Set<Integer> set = new HashSet<>();
        for (int num : arr) {
            if (set.contains(num + diff) || set.contains(num - diff)) {
                return true;
            }
            set.add(num);
        }
        return false;
    }

    // 5. 3Sum
    public static List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();
        for (int i = 0; i < nums.length && nums[i] <= 0; i++) {
            if (i == 0 || nums[i] != nums[i - 1]) {
                int left = i + 1, right = nums.length - 1;
                while (left < right) {
                    int sum = nums[i] + nums[left] + nums[right];
                    if (sum < 0) left++;
                    else if (sum > 0) right--;
                    else {
                        result.add(Arrays.asList(nums[i], nums[left++], nums[right--]));
                        while (left < right && nums[left] == nums[left - 1]) left++;
                    }
                }
            }
        }
        return result;
    }

    // 6. Intersection of Two Arrays
    public static int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> set1 = new HashSet<>();
        for (int n : nums1) set1.add(n);
        Set<Integer> resultSet = new HashSet<>();
        for (int n : nums2) {
            if (set1.contains(n)) resultSet.add(n);
        }
        return resultSet.stream().mapToInt(i -> i).toArray();
    }

    // 7. Intersection of Two Arrays II
    public static int[] intersect(int[] nums1, int[] nums2) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int n : nums1) map.put(n, map.getOrDefault(n, 0) + 1);
        List<Integer> result = new ArrayList<>();
        for (int n : nums2) {
            if (map.getOrDefault(n, 0) > 0) {
                result.add(n);
                map.put(n, map.get(n) - 1);
            }
        }
        return result.stream().mapToInt(i -> i).toArray();
    }

    // 8. Longest Substring with At Most Two Distinct Characters
    public static int lengthOfLongestSubstringTwoDistinct(String s) {
        int left = 0, maxLen = 0;
        Map<Character, Integer> map = new HashMap<>();
        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);
            map.put(c, map.getOrDefault(c, 0) + 1);
            while (map.size() > 2) {
                char leftChar = s.charAt(left);
                map.put(leftChar, map.get(leftChar) - 1);
                if (map.get(leftChar) == 0) map.remove(leftChar);
                left++;
            }
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    // 9. Longest Substring with At Most K Distinct Characters
    public static int lengthOfLongestSubstringKDistinct(String s, int k) {
        int left = 0, maxLen = 0;
        Map<Character, Integer> map = new HashMap<>();
        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);
            map.put(c, map.getOrDefault(c, 0) + 1);
            while (map.size() > k) {
                char leftChar = s.charAt(left);
                map.put(leftChar, map.get(leftChar) - 1);
                if (map.get(leftChar) == 0) map.remove(leftChar);
                left++;
            }
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    // 10. Longest Repeating Character Replacement
    public static int characterReplacement(String s, int k) {
        int[] count = new int[26];
        int maxCount = 0, left = 0, maxLen = 0;
        for (int right = 0; right < s.length(); right++) {
            count[s.charAt(right) - 'A']++;
            maxCount = Math.max(maxCount, count[s.charAt(right) - 'A']);
            while ((right - left + 1) - maxCount > k) {
                count[s.charAt(left) - 'A']--;
                left++;
            }
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    // 11. Find if There is a Subarray with 0 Sum
    public static boolean hasZeroSumSubarray(int[] arr) {
        Set<Integer> set = new HashSet<>();
        int sum = 0;
        for (int num : arr) {
            sum += num;
            if (sum == 0 || set.contains(sum)) return true;
            set.add(sum);
        }
        return false;
    }

    // 12. Subarray Sum Equals K
    public static int subarraySum(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        int sum = 0, count = 0;
        for (int num : nums) {
            sum += num;
            count += map.getOrDefault(sum - k, 0);
            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }
        return count;
    }

    // 13. Subarray Sums Divisible by K
    public static int subarraysDivByK(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        int sum = 0, count = 0;
        for (int num : nums) {
            sum += num;
            int mod = ((sum % k) + k) % k;
            count += map.getOrDefault(mod, 0);
            map.put(mod, map.getOrDefault(mod, 0) + 1);
        }
        return count;
    }

    // 14. Valid Anagram
    public static boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] count = new int[26];
        for (int i = 0; i < s.length(); i++) {
            count[s.charAt(i) - 'a']++;
            count[t.charAt(i) - 'a']--;
        }
        for (int c : count) {
            if (c != 0) return false;
        }
        return true;
    }

    public static void main(String[] args) {
        countFrequencies(new int[]{10, 20, 10, 5, 20});
        System.out.println(frequencySort("tree"));
        System.out.println(Arrays.toString(twoSum(new int[]{2, 7, 11, 15}, 9)));
        System.out.println(hasPairWithDifference(new int[]{5, 20, 3, 2, 50, 80}, 78));
        System.out.println(threeSum(new int[]{-1, 0, 1, 2, -1, -4}));
        System.out.println(Arrays.toString(intersection(new int[]{1, 2, 2, 1}, new int[]{2, 2})));
        System.out.println(Arrays.toString(intersect(new int[]{4, 9, 5}, new int[]{9, 4, 9, 8, 4})));
        System.out.println(lengthOfLongestSubstringTwoDistinct("eceba"));
        System.out.println(lengthOfLongestSubstringKDistinct("eceba", 2));
        System.out.println(characterReplacement("AABABBA", 1));
        System.out.println(hasZeroSumSubarray(new int[]{4, 2, -3, 1, 6}));
        System.out.println(subarraySum(new int[]{1, 1, 1}, 2));
        System.out.println(subarraysDivByK(new int[]{4, 5, 0, -2, -3, 1}, 5));
        System.out.println(isAnagram("anagram", "nagaram"));
    }
}





🔹 Introduction to Recursion (GFG)
🧠 What is Recursion?
Recursion is a technique where a function calls itself to solve smaller instances of the same problem. It must have:
•	Base Case: Stops the recursion.
•	Recursive Case: Calls itself with a smaller input.
📌 Example: Sum of first n natural numbers
Java
public static int sum(int n) {
    if (n == 0) return 0; // base case
    return n + sum(n - 1); // recursive case
}

________________________________________
🔹 Print 1 to 10 using Recursion
✅ Java Code:
Java
public class PrintNumbers {
    public static void print(int n) {
        if (n == 0) return;
        print(n - 1);
        System.out.print(n + " ");
    }

    public static void main(String[] args) {
        print(10); // Output: 1 2 3 4 5 6 7 8 9 10
    }
}

________________________________________
🔹 Factorial of a Number (GFG)
✅ Recursive Java Code:
Java
public class Factorial {
    public static int factorial(int n) {
        if (n == 0) return 1;
        return n * factorial(n - 1);
    }

    public static void main(String[] args) {
        System.out.println("Factorial of 5 is: " + factorial(5)); // Output: 120
    }
}

________________________________________
🔹 Sum of First N Natural Numbers (GFG)
✅ Recursive Java Code:
Java
public class SumNatural {
    public static int sum(int n) {
        if (n <= 1) return n;
        return n + sum(n - 1);
    }

    public static void main(String[] args) {
        System.out.println("Sum of first 5 natural numbers: " + sum(5)); // Output: 15
    }
}

________________________________________
🔹 Fibonacci Number (LeetCode 509)
✅ Java Code:
Java
public class Fibonacci {
    public static int fib(int n) {
        if (n <= 1) return n;
        return fib(n - 1) + fib(n - 2);
    }

    public static void main(String[] args) {
        System.out.println(fib(5)); // Output: 5
    }
}

________________________________________
🔹 Combination Sum (LeetCode 39)
✅ Java Code:
Java
public class CombinationSum {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
       <Integer>> res = new ArrayList<>();
        backtrack(candidates, target, 0, new ArrayList<>(), res);
        return res;
    }

    private void backtrack(int[] candidates, int target, int start, List<Integer> temp, List<List<Integer>> res) {
        if (target == 0) {
            res.add(new ArrayList<>(temp));
            return;
        }
        for (int i = start; i < candidates.length; i++) {
            if (candidates[i] <= target) {
                temp.add(candidates[i]);
               track(candidates, target - candidates[i], i, temp, res);
                temp.remove(temp.size() - 1);
            }
        }
    }
}

Show more lines
________________________________________
🔹 Combination Sum II (LeetCode 40)
✅ Java Code:
Java
public class CombinationSumII {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> res = new ArrayList<>();
        backtrack(candidates, target, 0, new ArrayList<>(), res);
        return res;
    }

    private void backtrack(int[] candidates, int target, int start, List<Integer> temp, List<List<Integer>> res) {
        if (target == 0) {
            res.add(new ArrayList<>(temp));
            return;
        }
        for (int i = start; i < candidates.length; i++) {
            if (i > start && candidates[i] == candidates[i - 1]) continue;
            if (candidates[i] > target) break;
            temp.add(candidates[i]);
            backtrack(candidates, target - candidates[i], i + 1, temp, res);
            temp.remove(temp.size() - 1);
        }
    }
}

Show more lines
________________________________________
🔹 Subsets (LeetCode 78)
✅ Java Code:
Java
public class Subsets {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        backtrack(0, nums, new ArrayList<>(), res);
        return res;
    }

    private void backtrack(int start, int[] nums, List<Integer> temp, List<List<Integer>> res) {
        res.add(new ArrayList<>(temp));
        for (int i = start; i < nums.length; i++) {
            temp.add(nums[i]);
            backtrack(i + 1, nums, temp, res);
            temp.remove(temp.size() - 1);
        }
    }
}

Show more lines
________________________________________
🔹 Subsets II (LeetCode 90)
✅ Java Code:
Java
public class SubsetsII {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        backtrack(0, nums, new ArrayList<>(), res);
        return res;
    }

    private void backtrack(int start, int[] nums, List<Integer> temp, List<List<Integer>> res) {
        res.add(new ArrayList<>(temp));
        for (int i = start; i < nums.length; i++) {
            if (i > start && nums[i] == nums[i - 1]) continue;
            temp.add(nums[i]);
            backtrack(i + 1, nums, temp, res);
            temp.remove(temp.size() - 1);
            temp.remove(temp.size() - 1);
        }
    }
}

🔹 1. Binary Tree Preorder Traversal (LeetCode 144)
Problem: Return the preorder traversal of a binary tree (Root → Left → Right).
✅ Java Solution:
Java
public List<Integer> preorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    preorder(root, result);
    return result;
}

private void preorder(TreeNode node, List<Integer> result) {
    if (node == null) return;
    result.add(node.val);
    preorder(node.left, result);
    preorder(node.right, result);
}

________________________________________
🔹 2. Binary Tree Inorder Traversal (LeetCode 94)
Problem: Return the inorder traversal (Left → Root → Right).
✅ Java Solution:
Java
public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    inorder(root, result);
    return result;
}

private void inorder(TreeNode node, List<Integer> result) {
    if (node == null) return;
    inorder(node.left, result);
    result.add(node.val);
    inorder(node.right, result);
}

________________________________________
🔹 3. Binary Tree Postorder Traversal (LeetCode 145)
Problem: Return the postorder traversal (Left → Right → Root).
✅ Java Solution:
Java
public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    postorder(root, result);
    return result;
}

private void postorder(TreeNode node, List<Integer> result) {
    if (node == null) return;
    postorder(node.left, result);
    postorder(node.right, result);
    result.add(node.val);
}

________________________________________
🔹 4. Search a Node in Binary Tree (GFG)
Problem: Search for a value in a binary tree (not BST).
✅ Java Solution:
Java
public boolean search(TreeNode root, int key) {
    if (root == null) return false;
    if (root.val == key) return true;
    return search(root.left, key) || search(root.right, key);
}

________________________________________
🔹 5. Sum of All Nodes in Binary Tree (GFG)
Problem: Return the sum of all node values.
✅ Java Solution:
Java
public int sumOfNodes(TreeNode root) {
    if (root == null) return 0;
    return root.val + sumOfNodes(root.left) + sumOfNodes(root.right);
}

________________________________________
🔹 6. Second Minimum Node in a Binary Tree (LeetCode 671)
Problem: Return the second smallest value in a special binary tree where each node has either 0 or 2 children and root.val = min(left.val, right.val).
✅ Java Solution:
Java
public int findSecondMinimumValue(TreeNode root) {
    if (root == null || root.left == null || root.right == null) return -1;

    int left = root.left.val;
    int right = root.right.val;

    if (left == root.val) left = findSecondMinimumValue(root.left);
    if (right == root.val) right = findSecondMinimumValue(root.right);

    if (left != -1 && right != -1) return Math.min(left, right);
    return (left != -1) ? left : right;
}

________________________________________
🔹 7. Find Maximum or Minimum in Binary Tree (GFG)
Problem: Find the maximum (or minimum) value in a binary tree.
✅ Java Solution:
Java
public int findMax(TreeNode root) {
    if (root == null) return Integer.MIN_VALUE;
    int leftMax = findMax(root.left);
    int rightMax = findMax(root.right);
    return Math.max(root.val, Math.max(leftMax, rightMax));
}

public int findMin(TreeNode root) {
    if (root == null) return Integer.MAX_VALUE;
    int leftMin = findMin(root.left);
    int rightMin = findMin(root.right);
    return Math.min(root.val, Math.min(leftMin, rightMin));
}

import java.util.*;

public class RecursionProblems {

    // 1. Print 1 to 10 using recursion
    public static void printOneToTen(int n) {
        if (n == 0) return;
        printOneToTen(n - 1);
        System.out.print(n + " ");
    }

    // 2. Factorial of a number
    public static int factorial(int n) {
        if (n == 0) return 1;
        return n * factorial(n - 1);
    }

    // 3. Sum of first N natural numbers
    public static int sumNatural(int n) {
        if (n <= 1) return n;
        return n + sumNatural(n - 1);
    }

    // 4. Fibonacci number
    public static int fibonacci(int n) {
        if (n <= 1) return n;
        return fibonacci(n - 1) + fibonacci(n - 2);
    }

    // 5. Combination Sum I
    public static List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> res = new ArrayList<>();
        backtrackCombinationSum(candidates, target, 0, new ArrayList<>(), res);
        return res;
    }

    private static void backtrackCombinationSum(int[] candidates, int target, int start, List<Integer> temp, List<List<Integer>> res) {
        if (target == 0) {
            res.add(new ArrayList<>(temp));
            return;
        }
        for (int i = start; i < candidates.length; i++) {
            if (candidates[i] <= target) {
                temp.add(candidates[i]);
                backtrackCombinationSum(candidates, target - candidates[i], i, temp, res);
                temp.remove(temp.size() - 1);
            }
        }
    }

    // 6. Combination Sum II
    public static List<List<Integer>> combinationSum2(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> res = new ArrayList<>();
        backtrackCombinationSum2(candidates, target, 0, new ArrayList<>(), res);
        return res;
    }

    private static void backtrackCombinationSum2(int[] candidates, int target, int start, List<Integer> temp, List<List<Integer>> res) {
        if (target == 0) {
            res.add(new ArrayList<>(temp));
            return;
        }
        for (int i = start; i < candidates.length; i++) {
            if (i > start && candidates[i] == candidates[i - 1]) continue;
            if (candidates[i] > target) break;
            temp.add(candidates[i]);
            backtrackCombinationSum2(candidates, target - candidates[i], i + 1, temp, res);
            temp.remove(temp.size() - 1);
        }
    }

    // 7. Subsets I
    public static List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        backtrackSubsets(0, nums, new ArrayList<>(), res);
        return res;
    }

    private static void backtrackSubsets(int start, int[] nums, List<Integer> temp, List<List<Integer>> res) {
        res.add(new ArrayList<>(temp));
        for (int i = start; i < nums.length; i++) {
            temp.add(nums[i]);
            backtrackSubsets(i + 1, nums, temp, res);
            temp.remove(temp.size() - 1);
        }
    }

    // 8. Subsets II
    public static List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();
        backtrackSubsetsWithDup(0, nums, new ArrayList<>(), res);
        return res;
    }

    private static void backtrackSubsetsWithDup(int start, int[] nums, List<Integer> temp, List<List<Integer>> res) {
        res.add(new ArrayList<>(temp));
        for (int i = start; i < nums.length; i++) {
            if (i > start && nums[i] == nums[i - 1]) continue;
            temp.add(nums[i]);
            backtrackSubsetsWithDup(i + 1, nums, temp, res);
            temp.remove(temp.size() - 1);
        }
    }

    public static void main(String[] args) {
        System.out.println("Print 1 to 10:");
        printOneToTen(10);
        System.out.println("\nFactorial of 5: " + factorial(5));
        System.out.println("Sum of first 5 natural numbers: " + sumNatural(5));
        System.out.println("Fibonacci of 5: " + fibonacci(5));

        int[] candidates1 = {2, 3, 6, 7};
        System.out.println("Combination Sum I for target 7: " + combinationSum(candidates1, 7));

        int[] candidates2 = {10, 1, 2, 7, 6, 1, 5};
        System.out.println("Combination Sum II for target 8: " + combinationSum2(candidates2, 8));

        int[] nums1 = {1, 2, 3};
        System.out.println("Subsets I: " + subsets(nums1));

        int[] nums2 = {1, 2, 2};
        System.out.println("Subsets II: " + subsetsWithDup(nums2));
    }
}


🔹 1. Maximum Depth of Binary Tree (LeetCode 104)
🧩 Problem:
Return the maximum depth (height) of a binary tree.
✅ Java Solution:
Java
public int maxDepth(TreeNode root) {
    if (root == null) return 0;
    return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
}

________________________________________
🔹 2. Balanced Binary Tree (LeetCode 110)
🧩 Problem:
Check if a binary tree is height-balanced (difference between left and right subtree heights is not more than 1).
✅ Java Solution:
Java
public boolean isBalanced(TreeNode root) {
    return checkHeight(root) != -1;
}

private int checkHeight(TreeNode node) {
    if (node == null) return 0;

    int left = checkHeight(node.left);
    int right = checkHeight(node.right);

    if (left == -1 || right == -1 || Math.abs(left - right) > 1) return -1;
    return 1 + Math.max(left, right);
}

________________________________________
🔹 3. Diameter of Binary Tree (LeetCode 543)
🧩 Problem:
Return the length of the longest path between any two nodes in the tree.
✅ Java Solution:
Java
int diameter = 0;

public int diameterOfBinaryTree(TreeNode root) {
    depth(root);
    return diameter;
}

private int depth(TreeNode node) {
    if (node == null) return 0;
    int left = depth(node.left);
    int right = depth(node.right);
    diameter = Math.max(diameter, left + right);
    return 1 + Math.max(left, right);
}

Show more lines
________________________________________
🔹 4. Same Tree (LeetCode 100)
🧩 Problem:
Check if two binary trees are structurally identical and have the same node values.
✅ Java Solution:
Java
public boolean isSameTree(TreeNode p, TreeNode q) {
    if (p == null && q == null) return true;
    if (p == null || q == null || p.val != q.val) return false;
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
}

________________________________________
🔹 5. Symmetric Tree (LeetCode 101)
🧩 Problem:
Check if a binary tree is a mirror of itself.
✅ Java Solution:
Java
public boolean isSymmetric(TreeNode root) {
    return isMirror(root.left, root.right);
}

private boolean isMirror(TreeNode t1, TreeNode t2) {
    if (t1 == null && t2 == null) return true;
    if (t1(TreeNode node) {
    if (node == null) return 0;

    int left = Math.max(maxGain(node.left), 0);
    int right = Math.max(maxGain(node.right), 0);

    int currentMax = node.val + left + right;
    maxSum = Math.max(maxSum, currentMax);

    return node.val + Math.max(left, right);
}

Show more lines
________________________________________
🔹 7. Binary Tree Zigzag Level Order Traversal (LeetCode 103)
🧩 Problem:
Return the level order traversal of a binary tree in zigzag (left-right, then right-left) order.
✅ Java Solution:
Java
public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) return result;

    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);
    boolean leftToRight = true;

    while (!queue.isEmpty()) {
        int size = queue.size();
        LinkedList<Integer> level = new LinkedList<>();

        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();
            if (leftToRight) level.addLast(node.val);
              else level.addFirst(node.val);

            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }

        result.add(level);
        leftToRight = !leftToRight;
    }

    return result;
}

🔹 1. Binary Tree Right Side View (LeetCode 199)
✅ Java Solution:
Java
public List<Integer> rightSideView(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    if (root == null) return result;

    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);

    while (!queue.isEmpty()) {
        int size = queue.size();
        TreeNode rightMost = null;

        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();
            rightMost = node;

            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }

        result.add(rightMost.val);
    }

    return result;
}

Show more lines
________________________________________
🔹 2. Left View of Binary Tree (GFG)
✅ Java Solution (DFS):
Java
void leftViewUtil(TreeNode node, int level, List<Integer> result) {
    if (node == null) return;

    if (level == result.size()) result.add(node.val);

    leftViewUtil(node.left, level + 1, result);
    leftViewUtil(node.right, level + 1, result);
}

public List<Integer> leftView(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    leftViewUtil(root, 0, result);
    return result;
}

Show more lines
________________________________________
🔹 3. Lowest Common Ancestor of a Binary Tree (LeetCode 236)
✅ Java Solution:
Java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) return root;

    TreeNode left = lowestCommonAncestor(root.left, p, q);
    TreeNode right = lowestCommonAncestor(root.right, p, q);

    if (left != null && right != null) return root;
    return left != null ? left : right;
}

________________________________________
🔹 4. Construct Binary Tree from Preorder and Inorder Traversal (LeetCode 105)
✅ Java Solution:
Java
public TreeNode buildTree(int[] preorder, int[] inorder) {
    Map<Integer, Integer> inMap = new HashMap<>();
    for (int i = 0; i < inorder.length; i++) {
        inMap.put(inorder[i], i);
    }

    return build(preorder, 0, preorder.length - 1, inorder, 0, inorder.length - 1, inMap);
}

private TreeNode build(int[] preorder, int preStart, int preEnd,
                      [] inorder, int inStart, int inEnd,
                       Map<Integer, Integer> inMap) {
    if (preStart > preEnd || inStart > inEnd) return null;

    TreeNode root = new TreeNode(preorder[preStart]);
    int inRoot = inMap.get(root.val);
    int numsLeft = inRoot - inStart;

    root.left = build(preorder, preStart + 1, preStart + numsLeft,
                      inorder, inStart, inRoot - 1, inMap);
    root.right = build(preorder, preStart + numsLeft + 1, preEnd,
                       inorder, inRoot + 1, inEnd, inMap);

    return root;
}

Show more lines
________________________________________
🔹 5. Construct Binary Tree from Inorder and Postorder Traversal (LeetCode 106)
✅ Java Solution:
Java
public TreeNode buildTree(int[] inorder, int[] postorder) {
    Map<Integer, Integer> inMap = new HashMap<>();
    for (int i = 0; i < inorder.length; i++) {
        inMap.put(inorder[i], i);
    }

    return build(postorder, 0, postorder.length - 1,
                 inorder, 0, inorder.length - 1, inMap);
}

private TreeNode build(int[] postorder, int postStart, int postEnd,
                       int[] inorder, int inStart, int inEnd,
                       Map<Integer, Integer> inMap) {
    if (postStart > postEnd || inStart > inEnd) return null;

    TreeNode root = new TreeNode(postorder[postEnd]);
    int inRoot = inMap.get(root.val);
    int numsLeft = inRoot - inStart;

    root.left = build(postorder, postStart, postStart + numsLeft - 1,
                      inorder, inStart, inRoot - 1, inMap);
    root.right = build(postorder, postStart + numsLeft, postEnd - 1,
                       inorder, inRoot + 1, inEnd, inMap);

    return root;
}

Show more lines
________________________________________
🔹 6. Binary Tree Level Order Traversal (LeetCode 102)
✅ Java Solution:
Java
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) return result;

    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);

    while (!queue.isEmpty()) {
        int size = queue.size();
        List<Integer> level = new ArrayList<>();

        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();
            level.add(node.val);
            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }

        result.add(level);
    }

    return result;
}

Show more lines
________________________________________
🔹 7. Binary Tree Level Order Traversal II (LeetCode 107)
✅ Java Solution:
Java
public List<List<Integer>> levelOrderBottom(TreeNode root) {
    LinkedList<List<Integer>> result = new LinkedList<>();
    if (root == null) return result;

    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);

    while (!queue.isEmpty()) {
        int size = queue.size();
        List<Integer> level = new ArrayList<>();

        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();
            level.add(node.val);
            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }

        result.addFirst(level);
    }

    return result;
}

Show more lines
________________________________________
🔹 8. Binary Tree Zigzag Level Order Traversal (LeetCode 103)
✅ Java Solution:
Java
public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) return result;

    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);
    boolean leftToRight = true;

    while (!queue.isEmpty()) {
        int size = queue.size();
        LinkedList<Integer> level = new LinkedList<>();

        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();
            if (leftToRight) level.addLast(node.val);
            else level.addFirst(node.val);

            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }
🔹 1. Search in a Binary Search Tree (LeetCode 700)
Java
public TreeNode searchBST(TreeNode root, int val) {
    if (root == null || root.val == val) return root;
    return val < root.val ? searchBST(root.left, val) : searchBST(root.right, val);
}

________________________________________
🔹 2. Minimum Element in BST (GFG)
Java
int minValue(Node root) {
    if (root == null) return -1;
    while (root.left != null) root = root.left;
    return root.data;
}

________________________________________
🔹 3. Maximum Element in BST (GFG)
Java
int maxValue(Node root) {
    if (root == null) return -1;
    while (root.right != null) root = root.right;
    return root.data;
}

________________________________________
🔹 4. Insert into a Binary Search Tree (LeetCode 701)
Java
public TreeNode insertIntoBST(TreeNode root, int val) {
    if (root == null) return new TreeNode(val);
    if (val < root.val) root.left = insertIntoBST(root.left, val);
    else root.right = insertIntoBST(root.right, val);
    return root;
}

________________________________________
🔹 5. Delete Node in a BST (LeetCode 450)
Java
public TreeNode deleteNode(TreeNode root, int key) {
    if (root == null) return null;

    if (key < root.val) root.left = deleteNode(root.left, key);
    else if (key > root.val) root.right = deleteNode(root.right, key);
    else {
        if (root.left == null) return root.right;
        if (root.right == null) return root.left;

        TreeNode minNode = findMin(root.right);
        root.val = minNode.val;
        root.right = deleteNode(root.right, minNode.val);
    }
    return root;
}

private TreeNode findMin(TreeNode node) {
    while (node.left != null) node = node.left;
    return node;
}

Show more lines
________________________________________
🔹 6. Range Sum of BST (LeetCode 938)
Java
public int rangeSumBST(TreeNode root, int low, int high) {
    if (root == null) return 0;
    if (root.val < low) return rangeSumBST(root.right, low, high);
    if (root.val > high) return rangeSumBST(root.left, low, high);
    return root.val + rangeSumBST(root.left, low, high) + rangeSumBST(root.right, low, high);
}

________________________________________
🔹 7. Increasing Order Search Tree (LeetCode 897)
Java
TreeNode newRoot = new TreeNode(0);
TreeNode current`

---

### 🔹 8. Kth Smallest Element in a BST (LeetCode 230)

```java
public int kthSmallest(TreeNode root, int k) {
    Stack<TreeNode> stack = new Stack<>();
    while (true) {
        while (root != null) {
            stack.push(root);
            root = root.left;
        }
        root = stack.pop();
        if (--k == 0) return root.val;
        root = root.right;
    }
}

Show more lines
________________________________________
🔹 9. Validate Binary Search Tree (LeetCode 98)
Java
public boolean isValidBST(TreeNode root) {
    return validate(root, null, null);
}

private boolean validate(TreeNode node, Integer low, Integer high) {
    if (node == null) return true;
    if ((low != null && node.val <= low) || (high != null && node.val >= high)) return false;
    return validate(node.left, low, node.val) && validate(node.right, node.val, high);
}

________________________________________
🔹 10. Lowest Common Ancestor of a BST (LeetCode 235)
Java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (p.val < root.val && q.val < root.val)
        return lowestCommonAncestor(root.left, p, q);
    else if (p.val > root.val && q.val > root.val)
        return lowestCommonAncestor(root.right, p, q);
    else
        return root;
}

________________________________________
import java.util.*;

class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int x) { val = x; }
}

public class BSTProblems {

    // 1. Validate Binary Search Tree
    public boolean isValidBST(TreeNode root) {
        return validate(root, null, null);
    }

    private boolean validate(TreeNode node, Integer low, Integer high) {
        if (node == null) return true;
        if ((low != null && node.val <= low) || (high != null && node.val >= high)) return false;
        return validate(node.left, low, node.val) && validate(node.right, node.val, high);
    }

    // 2. Lowest Common Ancestor of a BST
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (p.val < root.val && q.val < root.val)
            return lowestCommonAncestor(root.left, p, q);
        else if (p.val > root.val && q.val > root.val)
            return lowestCommonAncestor(root.right, p, q);
        else
            return root;
    }

    // 3. Construct BST from Preorder Traversal
    public TreeNode bstFromPreorder(int[] preorder) {
        return buildBST(preorder, new int[]{0}, Integer.MAX_VALUE);
    }

    private TreeNode buildBST(int[] preorder, int[] index, int bound) {
        if (index[0] == preorder.length || preorder[index[0]] > bound) return null;
        TreeNode root = new TreeNode(preorder[index[0]++]);
        root.left = buildBST(preorder, index, root.val);
        root.right = buildBST(preorder, index, bound);
        return root;
    }

    // 4. Inorder Successor in BST
    public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
        TreeNode successor = null;
        while (root != null) {
            if (p.val < root.val) {
                successor = root;
                root = root.left;
            } else {
                root = root.right;
            }
        }
        return successor;
    }

    // 5. Two Sum IV - Input is a BST
    public boolean findTarget(TreeNode root, int k) {
        Set<Integer> set = new HashSet<>();
        return dfsFind(root, k, set);
    }

    private boolean dfsFind(TreeNode node, int k, Set<Integer> set) {
        if (node == null) return false;
        if (set.contains(k - node.val)) return true;
        set.add(node.val);
        return dfsFind(node.left, k, set) || dfsFind(node.right, k, set);
    }

    // 6. Balance a BST
    public TreeNode balanceBST(TreeNode root) {
        List<Integer> nodes = new ArrayList<>();
        inorder(root, nodes);
        return buildBalancedBST(nodes, 0, nodes.size() - 1);
    }

    private void inorder(TreeNode node, List<Integer> nodes) {
        if (node == null) return;
        inorder(node.left, nodes);
        nodes.add(node.val);
        inorder(node.right, nodes);
    }

    private TreeNode buildBalancedBST(List<Integer> nodes, int start, int end) {
        if (start > end) return null;
        int mid = (start + end) / 2;
        TreeNode root = new TreeNode(nodes.get(mid));
        root.left = buildBalancedBST(nodes, start, mid - 1);
        root.right = buildBalancedBST(nodes, mid + 1, end);
        return root;
    }

    // Helper method to print inorder traversal
    public void printInorder(TreeNode root) {
        if (root == null) return;
        printInorder(root.left);
        System.out.print(root.val + " ");
        printInorder(root.right);
    }

    // Main method with test cases
    public static void main(String[] args) {
        BSTProblems bst = new BSTProblems();

        // Construct BST manually
        TreeNode root = new TreeNode(5);
        root.left = new TreeNode(3);
        root.right = new TreeNode(7);
        root.left.left = new TreeNode(2);
        root.left.right = new TreeNode(4);
        root.right.left = new TreeNode(6);
        root.right.right = new TreeNode(8);

        // 1. Validate BST
        System.out.println("Is valid BST: " + bst.isValidBST(root));

        // 2. Lowest Common Ancestor
        TreeNode p = root.left; // 3
        TreeNode q = root.right; // 7
        TreeNode lca = bst.lowestCommonAncestor(root, p, q);
        System.out.println("Lowest Common Ancestor of " + p.val + " and " + q.val + ": " + lca.val);

        // 3. Construct BST from Preorder
        int[] preorder = {5, 3, 2, 4, 7, 6, 8};
        TreeNode constructed = bst.bstFromPreorder(preorder);
        System.out.print("Constructed BST (inorder): ");
        bst.printInorder(constructed);
        System.out.println();

        // 4. Inorder Successor
        TreeNode successor = bst.inorderSuccessor(root, root.left); // successor of 3
        System.out.println("Inorder Successor of " + root.left.val + ": " + (successor != null ? successor.val : "null"));

        // 5. Two Sum IV
        System.out.println("Find target 9 in BST: " + bst.findTarget(root, 9)); // 2 + 7

        // 6. Balance BST
        TreeNode unbalanced = new TreeNode(1);
        unbalanced.right = new TreeNode(2);
        unbalanced.right.right = new TreeNode(3);
        unbalanced.right.right.right = new TreeNode(4);
        TreeNode balanced = bst.balanceBST(unbalanced);
        System.out.print("Balanced BST (inorder): ");
        bst.printInorder(balanced);
        System.out.println();
    }
}


Q.)Dynamic Programming:-
import java.util.*;

public class DynamicProgrammingProblems {

    // 1. Climbing Stairs
    public static int climbStairs(int n) {
        if (n <= 2) return n;
        int a = 1, b = 2;
        for (int i = 3; i <= n; i++) {
            int temp = a + b;
            a = b;
            b = temp;
        }
        return b;
    }

    // 2. Min Cost Climbing Stairs
    public static int minCostClimbingStairs(int[] cost) {
        int n = cost.length;
        int[] dp = new int[n + 1];
        for (int i = 2; i <= n; i++) {
            dp[i] = Math.min(dp[i - 1] + cost[i - 1], dp[i - 2] + cost[i - 2]);
        }
        return dp[n];
    }

    // 3. House Robber
    public static int rob(int[] nums) {
        if (nums.length == 0) return 0;
        if (nums.length == 1) return nums[0];
        int[] dp = new int[nums.length];
        dp[0] = nums[0];
        dp[1] = Math.max(nums[0], nums[1]);
        for (int i = 2; i < nums.length; i++) {
            dp[i] = Math.max(dp[i - 1], dp[i - 2] + nums[i]);
        }
        return dp[nums.length - 1];
    }

    // 4. 0-1 Knapsack
    public static int knapsack(int W, int[] wt, int[] val, int n) {
        int[][] dp = new int[n + 1][W + 1];
        for (int i = 0; i <= n; i++) {
            for (int w = 0; w <= W; w++) {
                if (i == 0 || w == 0) dp[i][w] = 0;
                else if (wt[i - 1] <= w)
                    dp[i][w] = Math.max(val[i - 1] + dp[i - 1][w - wt[i - 1]], dp[i - 1][w]);
                else
                    dp[i][w] = dp[i - 1][w];
            }
        }
        return dp[n][W];
    }

    // 5. Coin Change
    public static int coinChange(int[] coins, int amount) {
        int max = amount + 1;
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, max);
        dp[0] = 0;
        for (int coin : coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] = Math.min(dp[i], dp[i - coin] + 1);
            }
        }
        return dp[amount] == max ? -1 : dp[amount];
    }

    // 6. Coin Change 2
    public static int change(int amount, int[] coins) {
        int[] dp = new int[amount + 1];
        dp[0] = 1;
        for (int coin : coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] += dp[i - coin];
            }
        }
        return dp[amount];
    }

    // 7. Unique Paths
    public static int uniquePaths(int m, int n) {
        int[][] dp = new int[m][n];
        for (int i = 0; i < m; i++) dp[i][0] = 1;
        for (int j = 0; j < n; j++) dp[0][j] = 1;
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
            }
        }
        return dp[m - 1][n - 1];
    }

    // 8. Best Time to Buy and Sell Stock I
    public static int maxProfitI(int[] prices) {
        int minPrice = Integer.MAX_VALUE, maxProfit = 0;
        for (int price : prices) {
            minPrice = Math.min(minPrice, price);
            maxProfit = Math.max(maxProfit, price - minPrice);
        }
        return maxProfit;
    }

    // 9. Best Time to Buy and Sell Stock II
    public static int maxProfitII(int[] prices) {
        int profit = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i - 1])
                profit += prices[i] - prices[i - 1];
        }
        return profit;
    }

    // 10. Best Time to Buy and Sell Stock III
    public static int maxProfitIII(int[] prices) {
        int buy1 = Integer.MIN_VALUE, buy2 = Integer.MIN_VALUE;
        int sell1 = 0, sell2 = 0;
        for (int price : prices) {
            buy1 = Math.max(buy1, -price);
            sell1 = Math.max(sell1, buy1 + price);
            buy2 = Math.max(buy2, sell1 - price);
            sell2 = Math.max(sell2, buy2 + price);
        }
        return sell2;
    }

    // 11. Best Time to Buy and Sell Stock IV
    public static int maxProfitIV(int k, int[] prices) {
        if (prices.length == 0 || k == 0) return 0;
        if (k >= prices.length / 2) return maxProfitII(prices);

        int[][] dp = new int[k + 1][prices.length];
        for (int i = 1; i <= k; i++) {
            int maxDiff = -prices[0];
            for (int j = 1; j < prices.length; j++) {
                dp[i][j] = Math.max(dp[i][j - 1], prices[j] + maxDiff);
                maxDiff = Math.max(maxDiff, dp[i - 1][j] - prices[j]);
            }
        }
        return dp[k][prices.length - 1];
    }

    public static void main(String[] args) {
        System.out.println("Climb Stairs (5): " + climbStairs(5));
        System.out.println("Min Cost Climbing Stairs: " + minCostClimbingStairs(new int[]{10, 15, 20}));
        System.out.println("House Robber: " + rob(new int[]{2, 7, 9, 3, 1}));
        System.out.println("0-1 Knapsack: " + knapsack(50, new int[]{10, 20, 30}, new int[]{60, 100, 120}, 3));
        System.out.println("Coin Change: " + coinChange(new int[]{1, 2, 5}, 11));
        System.out.println("Coin Change 2: " + change(5, new int[]{1, 2, 5}));
        System.out.println("Unique Paths (3x7): " + uniquePaths(3, 7));
        System.out.println("Max Profit I: " + maxProfitI(new int[]{7, 1, 5, 3, 6, 4}));
        System.out.println("Max Profit II: " + maxProfitII(new int[]{7, 1, 5, 3, 6, 4}));
        System.out.println("Max Profit III: " + maxProfitIII(new int[]{3,3,5,0,0,3,1,4}));
        System.out.println("Max Profit IV (k=2): " + maxProfitIV(2, new int[]{3,2,6,5,0,3}));
    }
}


Q.)Binary Search:-
import java.util.*;

public class BinarySearchProblems {

    // 1. Binary Search (GFG / LeetCode)
    public static int binarySearch(int[] arr, int target) {
        int left = 0, right = arr.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (arr[mid] == target) return mid;
            else if (arr[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        return -1;
    }

    // 2. Search Insert Position (LeetCode 35)
    public static int searchInsert(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) return mid;
            else if (nums[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        return left;
    }

    // 3. Search a 2D Matrix (LeetCode 74)
    public static boolean searchMatrix(int[][] matrix, int target) {
        if (matrix.length == 0 || matrix[0].length == 0) return false;
        int rows = matrix.length, cols = matrix[0].length;
        int left = 0, right = rows * cols - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            int midVal = matrix[mid / cols][mid % cols];
            if (midVal == target) return true;
            else if (midVal < target) left = mid + 1;
            else right = mid - 1;
        }
        return false;
    }

    // 4. Sqrt(x) (LeetCode 69)
    public static int mySqrt(int x) {
        if (x < 2) return x;
        int left = 1, right = x / 2;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            long square = (long) mid * mid;
            if (square == x) return mid;
            else if (square < x) left = mid + 1;
            else right = mid - 1;
        }
        return right;
    }

    // 5. Find First and Last Position of Element in Sorted Array (LeetCode 34)
    public static int[] searchRange(int[] nums, int target) {
        int first = findBound(nums, target, true);
        int last = findBound(nums, target, false);
        return new int[]{first, last};
    }

    private static int findBound(int[] nums, int target, boolean isFirst) {
        int left = 0, right = nums.length - 1, bound = -1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) {
                bound = mid;
                if (isFirst) right = mid - 1;
                else left = mid + 1;
            } else if (nums[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        return bound;
    }

    // Main method with test cases
    public static void main(String[] args) {
        // Binary Search
        int[] arr = {1, 3, 5, 7, 9};
        System.out.println("Binary Search: " + binarySearch(arr, 5)); // Output: 2

        // Search Insert Position
        System.out.println("Search Insert Position: " + searchInsert(arr, 6)); // Output: 3

        // Search a 2D Matrix
        int[][] matrix = {
            {1, 3, 5},
            {7, 9, 11},
            {13, 15, 17}
        };
        System.out.println("Search Matrix: " + searchMatrix(matrix, 9)); // Output: true

        // Sqrt(x)
        System.out.println("Sqrt of 16: " + mySqrt(16)); // Output: 4

        // Find First and Last Position
        int[] nums = {5, 7, 7, 8, 8, 10};
        System.out.println("Search Range: " + Arrays.toString(searchRange(nums, 8))); // Output: [3, 4]
    }
}
