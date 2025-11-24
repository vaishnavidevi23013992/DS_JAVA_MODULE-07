# Flattening a Nested List Using an Iterator
## DATE:
## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).
## Algorithm

1. Take the nested list input where each element may be an integer or another nested list.
2. Use a stack to store elements in reverse order so that the first integer appears on top.
3. While processing, if the top element is a list, expand it by pushing its elements onto the stack in reverse order.
4. If the top element is an integer, it is ready to be returned by next(), and hasNext() should return true.
5. Continue flattening until all integers are processed sequentially so the iterator can return them one by one.
 

## Program:
```
Program to find Flattening a Nested List Using an Iterator
Developed by: VAISHNAVIDEVI V
RegisterNumber:  212223040230
```
```
import java.util.*;

// Dummy implementation of NestedInteger so the program runs
class SimpleNestedInteger implements NestedInteger {
    private Integer value;
    private List<NestedInteger> list;

    // Constructor for a single integer
    public SimpleNestedInteger(int value) {
        this.value = value;
        this.list = null;
    }

    // Constructor for a list
    public SimpleNestedInteger(List<NestedInteger> list) {
        this.list = list;
        this.value = null;
    }

    public boolean isInteger() {
        return value != null;
    }

    public Integer getInteger() {
        return value;
    }

    public List<NestedInteger> getList() {
        return list;
    }
}

// Given Interface (do NOT modify)
interface NestedInteger {
    boolean isInteger();
    Integer getInteger();
    List<NestedInteger> getList();
}

// Flatten Iterator Class
class NestedIterator implements Iterator<Integer> {

    private Stack<NestedInteger> stack = new Stack<>();

    public NestedIterator(List<NestedInteger> nestedList) {
        for (int i = nestedList.size() - 1; i >= 0; i--) {
            stack.push(nestedList.get(i));
        }
    }

    public Integer next() {
        return stack.pop().getInteger();
    }

    public boolean hasNext() {
        while (!stack.isEmpty()) {
            NestedInteger top = stack.peek();

            if (top.isInteger()) return true;

            stack.pop();
            List<NestedInteger> list = top.getList();

            for (int i = list.size() - 1; i >= 0; i--) {
                stack.push(list.get(i));
            }
        }
        return false;
    }
}

// MAIN CLASS (compiler will run THIS, so no errors)
public class Main {
    public static void main(String[] args) {

        // Creating nested list: [1,[4,[6]]]
        List<NestedInteger> nested = new ArrayList<>();
        nested.add(new SimpleNestedInteger(1));

        List<NestedInteger> level2 = new ArrayList<>();
        level2.add(new SimpleNestedInteger(4));

        List<NestedInteger> level3 = new ArrayList<>();
        level3.add(new SimpleNestedInteger(6));

        level2.add(new SimpleNestedInteger(level3));
        nested.add(new SimpleNestedInteger(level2));

        // Using iterator
        NestedIterator it = new NestedIterator(nested);

        System.out.print("Flattened Output: ");
        while (it.hasNext()) {
            System.out.print(it.next() + " ");
        }
    }
}


```

## Output:

<img width="1919" height="619" alt="image" src="https://github.com/user-attachments/assets/a34e70d1-84cb-4065-b96e-c6b2aef61415" />


## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.
