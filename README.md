# string-to-integer-atoi-
public class Solution {
    public int myAtoi(String s) {
        // Ignore leading whitespace
        int i = 0;
        while (i < s.length() && s.charAt(i) == ' ') {
            i++;
        }
        
        // Check if the number is positive or negative
        int sign = 1;
        if (i < s.length() && (s.charAt(i) == '+' || s.charAt(i) == '-')) {
            sign = (s.charAt(i++) == '-') ? -1 : 1;
        }
        
        // Read digits and convert to integer
        int result = 0;
        while (i < s.length() && Character.isDigit(s.charAt(i))) {
            int digit = s.charAt(i++) - '0';
            
            // Check for overflow
            if (result > Integer.MAX_VALUE / 10 || (result == Integer.MAX_VALUE / 10 && digit > 7)) {
                return (sign == 1) ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }
            
            result = result * 10 + digit;
        }
        
        return result * sign;
    }
    
    public static void main(String[] args) {
        Solution solution = new Solution();
        
        // Test cases
        System.out.println(solution.myAtoi("42")); // Output: 42
        System.out.println(solution.myAtoi("   -42")); // Output: -42
        System.out.println(solution.myAtoi("4193 with words")); // Output: 4193
    }
}
