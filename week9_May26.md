# Week 9 Lab Report
## Part 1: Debugging Scenario
### a) Student's Orignial Post
I wrote a code that contains a class <code>lab9</code>, which includes the method <code>sort_min()</code> and <code>sort_max()</code>.
<br> However, if I run the tester methods, both <code>sort_min()</code> and <code>sort_max()</code> gives me a weird output of arraylist with duplicate elements, as it can be seen below.
<br> I am sure there is something wrong on the way I sort the arraylist, but I have no idea where to fix.

<br>Code for <code>lab9.java</code>
```

import java.util.ArrayList;

/**
 * the lab9 class stores instance variable arr
 * and class methods
 */
public class lab9 <E extends Comparable>{
    ArrayList<E> arr;

    /** Constrcutor method
     * for no argument
     */
    public lab9(){
        arr = new ArrayList<>();
    }

    /** Constrcutor method
     * with argument arraylist
     * initializes this.arr as arr
     * @param arr - initial arraylist
     */
    public lab9(ArrayList<E> arr){
        this.arr = arr;
    }

    /**
     * the method returns an arrraylist
     * where instance var arr is sorted from min to max
     * @return sorted arraylist
     */
    public ArrayList<E> sort_min(){
        // create new arraylist to sorted element
        ArrayList<E> sorted = new ArrayList<>(arr.size());

        for(int curr_idx=0;curr_idx<arr.size();curr_idx++){
            int min_idx = curr_idx; 
            for(int comp_idx=curr_idx+1;comp_idx<arr.size();comp_idx++){
                if(arr.get(comp_idx).compareTo((E) arr.get(min_idx))<0){
                    min_idx=comp_idx;
                }
            }
            sorted.add((E) arr.get(min_idx));
        }

        return sorted;
    }

    /**
     * the method returns an arrraylist
     * where instance var arr is sorted from max to min
     * @return sorted arraylist
     */
    public ArrayList<E> sort_max(){
        // create new arraylist to sorted element
        ArrayList<E> sorted = new ArrayList<>(arr.size());

        for(int curr_idx=0;curr_idx<arr.size();curr_idx++){
            int max_idx = curr_idx; 
            for(int comp_idx=curr_idx+1;comp_idx<arr.size();comp_idx++){
                if(arr.get(comp_idx).compareTo((E) arr.get(max_idx))>0){
                    max_idx=comp_idx;
                }
            }
            sorted.add((E) arr.get(max_idx));
        }

        return sorted;
    }
}

```

<br>Code for <code>lab9Tester.java</code>

```

import org.junit.Before;
import org.junit.Test;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

import static org.junit.Assert.*;


public class lab9Tester {
    ArrayList<String> arr_empty
        = new ArrayList<>();
    ArrayList<String> arr_sorted
        = new ArrayList<>(Arrays.asList("a","b","c","d","e"));
    ArrayList<String> arr_reversed
        = new ArrayList<>(Arrays.asList("e","d","c","b","a"));
    ArrayList<String> arr_random
        = new ArrayList<>(Arrays.asList("c","a","b","d","e"));
    
    ArrayList<String> minSort_expected
        = new ArrayList<>(Arrays.asList("a","b","c","d","e"));
    ArrayList<String> maxSort_expected
        = new ArrayList<>(Arrays.asList("e","d","c","b","a"));


    lab9<String> comp_sorted,
        comp_reversed,
        comp_random,
        comp_empty;

    @Before
    public void setUp(){
        comp_empty = new lab9<>(arr_empty);
        comp_sorted = new lab9<>(arr_sorted);
        comp_reversed = new lab9<>(arr_reversed);
        comp_random = new lab9<>(arr_random);
    }

    @Test
    public void test_sortMin(){
        assertEquals(new ArrayList<>(), comp_empty.sort_min());
        assertEquals(minSort_expected, comp_sorted.sort_min());
        assertEquals(minSort_expected, comp_reversed.sort_min());
        assertEquals(minSort_expected, comp_random.sort_min());
    }

    @Test
    public void test_sortMax(){
        assertEquals(new ArrayList<>(), comp_empty.sort_max());
        assertEquals(maxSort_expected, comp_reversed.sort_max());
        assertEquals(maxSort_expected, comp_random.sort_max());
        assertEquals(maxSort_expected, comp_sorted.sort_max());
    }
}

```

<br>Code for <code>grade.sh</code>

```

CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm junit-output.txt
rm result.txt

if [[ -f lab9.java ]]
then
    echo "lab9.java file found"
else
    echo "lab9.java file not found"
    echo "Grade: 0"
    exit
fi

javac -cp $CPATH *.java
echo "The exit code for the compile step is $?"

# check for failures 
if [ $? -eq 0 ]; then 
    echo 'no exception while running test'
else 
    echo 'exception while running test'
fi

java -cp $CPATH org.junit.runner.JUnitCore lab9Tester | grep "Tests run: " > junit-output.txt
java -cp $CPATH org.junit.runner.JUnitCore lab9Tester | grep "\S" > result.txt

FAILS=$(cat junit-output.txt | cut -d':' -f 3 | cut -d' ' -f 2)
TOTAL=$(cat junit-output.txt | cut -d':' -f 2 | cut -d',' -f 1| cut -d' ' -f 2)

if [[ $FAILS -gt 0 ]]
    then
        echo "Numbers failed: $FAILS/$TOTAL"
        echo "-----"
        cat result.txt |tail -n +5| while read -r line ; do
            if [[ $line != at* ]]; then
                echo $line
            fi
        done

    else
    echo "Grade:100"
fi

```

<br>What I get after running <code>grade.sh</code>
```

(base) ➜  lab9 git:(master) ✗ bash grade.sh                           
lab9.java file found
Note: lab9.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
The exit code for the compile step is 0
no exception while running test
Numbers failed: 2/2
-----
1) test_sortMax(lab9Tester)
java.lang.AssertionError: expected:<[e, d, c, b, a]> but was:<[e, e, e, e, e]>
2) test_sortMin(lab9Tester)
java.lang.AssertionError: expected:<[a, b, c, d, e]> but was:<[a, a, a, a, a]>
FAILURES!!!
Tests run: 2, Failures: 2

```

### b) TA response
I expect you are trying to use an algorithm that looks similar with selection sort. However, since you didn't delete the selected element after each loop. That is why you are getting duplicate elements. 
<br> For example, if applying your code in     
```
ArrayList<String> arr_random
        = new ArrayList<>(Arrays.asList("c","a","b","d","e"));
```
, <code>min_idx</code> in the first loop would be 1, which is the index of <code>"a"</code> in <code>arr</code>. After going through the first loop, the status of the variable would be:
```
ArrayList<String> sorted = {"a"}
min_idx = 1
curr_idx = 1
```
Thus, the code will start seraching for the minimum element from index 1 to the last index, while "a" exists between the index. Thus, the code will add <code>"a"</code> again to the <code>sorted</code>. 

<br> If you want to stick on creating a new sorted array instead of sorting arr itself, I would recommend editing <code>lab9.java</code> like below:
```

import java.util.ArrayList;

/**
 * the lab9 class stores instance variable arr
 * and class methods
 */
public class lab9 <E extends Comparable>{
    ArrayList<E> arr;

    /** Constrcutor method
     * for no argument
     */
    public lab9(){
        arr = new ArrayList<>();
    }

    /** Constrcutor method
     * with argument arraylist
     * initializes this.arr as arr
     * @param arr - initial arraylist
     */
    public lab9(ArrayList<E> arr){
        this.arr = arr;
    }

    /**
     * the method returns an arrraylist
     * where instance var arr is sorted from min to max
     * @return sorted arraylist
     */
    public ArrayList<E> sort_min(){
        // create new arraylist to sorted element
        ArrayList<E> sorted = (ArrayList<E>) arr.clone();
        E temp;

        for(int curr_idx=0;curr_idx<sorted.size();curr_idx++){
            int min_idx = curr_idx; 
            for(int comp_idx=curr_idx+1;comp_idx<sorted.size();comp_idx++){
                // elem in comp_idx is smaller than elem in min_idx
                if(sorted.get(comp_idx).compareTo((E) sorted.get(min_idx))<0){
                    min_idx=comp_idx;
                }
            }

            // swap two elements
            temp = sorted.get(curr_idx);
            sorted.set(curr_idx, sorted.get(min_idx));
            sorted.set(min_idx, temp);
        }

        return sorted;
    }

    /**
     * the method returns an arrraylist
     * where instance var arr is sorted from max to min
     * @return sorted arraylist
     */
    public ArrayList<E> sort_max(){
        // create new arraylist to sorted element
        ArrayList<E> sorted = (ArrayList<E>) arr.clone();
        E temp;

        for(int curr_idx=0;curr_idx<sorted.size();curr_idx++){
            int max_idx = curr_idx; 
            for(int comp_idx=curr_idx+1;comp_idx<sorted.size();comp_idx++){
                // elem in comp_idx is smaller than elem in min_idx
                if(sorted.get(comp_idx).compareTo((E) sorted.get(max_idx))>0){
                    max_idx=comp_idx;
                }
            }

            // swap two elements
            temp = sorted.get(curr_idx);
            sorted.set(curr_idx, sorted.get(max_idx));
            sorted.set(max_idx, temp);
        }

        return sorted;
    }
}
```
The method now shallow-copies <code>arr</code> to <code>sorted</code>, then conducts selection sort in <code>sorted</code>.


## Part 2 – Reflection
In general, I learned how to use bash commands, including ways to access and extract informations from files and directories, and utilziing them within the bash files. Furthermore, I learned how to edit the file without auctally openeing the file in visual code using vim operations. Lastly, I learned how to use java debugger, especially the way to cope with infinite loop.
<br> It was interesting to learn how gradescope acts. It was challenging to consider all edge cases, but I believe it was a valuable experince which incresed by knowledge using bash commands.
