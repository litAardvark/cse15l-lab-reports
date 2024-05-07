# **LAB REPORT 3**
# PART 1
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
![Screenshot test run](symptom.png)

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
## Explanation of code fix
The bug in the original code was that the method was overwriting the data in the array too early. By cloning the orginal array, I kept the orginal data which could be placed in the array in reverse.

# PART 2
## Command: `grep`
`-w`
```
$ grep -w "terrorist" 911report/chapter-1.txt
At the same time or shortly thereafter, Atta-the only terrorist on board trained to fly a jet-would have moved to the cockpit...
```
```
$ grep -w "virus" biomed/1471-2091-3-14.txt
        immunodeficiency virus type 1 (HIV-1) Tat research has
        to be reduced upon infection with the wild-type LAI virus
        or a Tat exon one recombinant virus [ 12 13 ] .
.
.
.
```

The `-w` option tells the `grep` command to find matches that are complete words. It ignores words that contain the input pattern and only returns lines the full word. This is useful when looking for a specific word and not fragments. (_Source: https://man7.org/linux/man-pages/man1/grep.1.html_)

`-c`
```
$ grep -c "terrorism" 911report/chapter-1.txt
1
```
```
$ grep -c "virus" biomed/1471-2091-3-14.txt
19
```
The `-c` option tells `grep` to count the lines in which the pattern appears in the given file. This is useful when you only care to find how many lines contain a specified word. (_Source: https://man7.org/linux/man-pages/man1/grep.1.html_)

`-m [num]`
```
$ grep -m 5 "virus" biomed/1471-2091-3-14.txt
        immunodeficiency virus type 1 (HIV-1) Tat research has
        to be reduced upon infection with the wild-type LAI virus
        or a Tat exon one recombinant virus [ 12 13 ] .
          infection by the same or other viruses that use the CD4
          selective entry and replication of CCR5 virus into cells
```
```
$ grep -m 1 "hijack" 911report/chapter-1.txt
    In passing through these checkpoints, each of the hijackers would have been screened by a walk-through metal detector calibrated to ....
```
The `-m [num]` option tells `grep` to print the first [num] lines the text appears in. This is useful for limiting the number of matches printed to the screen. (_Source: https://man7.org/linux/man-pages/man1/grep.1.html_)

`-n`
```
$ grep -n "virus" biomed/1471-2091-3-14.txt
26:        immunodeficiency virus type 1 (HIV-1) Tat research has
41:        to be reduced upon infection with the wild-type LAI virus
42:        or a Tat exon one recombinant virus [ 12 13 ] .
154:          infection by the same or other viruses that use the CD4
174:          selective entry and replication of CCR5 virus into cells
187:          better entry and infection of the CCR5 (R5) virus into
190:          of the R5 than the CXCR4 (X4) virus. The increase in
192:          the R5 virus, further implying that the CCR5 co-receptor
193:          allowed a better selection of R5 virus in Tat expressing
212:          class of virus (CCR5) over another (CXCR4).
278:          translation and replication. For instance, viruses
279:          including Herpes simplex virus type 1 (HSV-1) have been
288:          ] . This poses an immense challenge for the virus to be
291:          Therefore, it would be advantageous for the virus to set
327:          virus [ 22 ] . Along these lines, a Tat peptide
397:          RNA) and not the whole virus (all three classes of the
419:          latent HIV-1 virus. For instance, the signal transduction
446:          subsequent infection by other viruses.
748:          capable of making infectious virus in presence of TNF,
```

```
$ grep -n  "air defense" 911report/chapter-1.txt
230:    The threat of Soviet bombers diminished significantly as the Cold War ended, and the number of NORAD alert sites was reduced from its Cold War high of 26. Some within the Pentagon argued in the 1990s that the alert sites should be eliminated entirely. In an effort to preserve their mission, members of the air defense community advocated the importance of air sovereignty against emerging "asymmetric threats" to the United States: drug smuggling, "non-state and state-sponsored terrorists," and the proliferation of weapons of mass destruction and ballistic missile technology.
298:    NEADS ordered to battle stations the two F-15 alert aircraft at Otis Air Force Base in Falmouth, Massachusetts, 153 miles away from New York City. The air defense of America began with this call.
```
The `-n` option tells `grep` to print the line number for each match found. This is useful for narrowing down where specifically in a file a match is found.(_Source: https://man7.org/linux/man-pages/man1/grep.1.html_)
