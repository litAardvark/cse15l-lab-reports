# **LAB REPORT 1**
## Bug: ArrayExamples.reverseInPlace()
## Failure-inducing input
```
import static org.junit.Assert.assertArrayEquals;
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class ArrayTestsForLabReport {
@Test
    public void testReverseInPlaceFailureInducing() {
        int[] input1 = { 1, 2, 3, 4, 5 };
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[] { 5, 4, 3, 2, 1 }, input1);
    }
.
.
.
}
```
## Passing input
```
import static org.junit.Assert.assertArrayEquals;
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class ArrayTestsForLabReport {
.
.
.
   @Test
    public void testReverseInPlacePass() {
        int[] input1 = { 1, 1, 2, 1, 1 };
        ArrayExamples.reverseInPlace(input1);
        assertArrayEquals(new int[] { 1, 1, 2, 1, 1 }, input1);
    }
}
```
## Symptom
\
\

## Buggy Code
```
  static void reverseInPlace(int[] arr) {
    for (int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

## Fixed code
```
  static void reverseInPlace(int[] arr) {
   int[] original = arr.clone();
    for (int i = 0; i < arr.length; i += 1) {
      arr[i] = original[arr.length - i - 1];
    }
  }
```
