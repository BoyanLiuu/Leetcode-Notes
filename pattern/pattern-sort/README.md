# Pattern Sort

## Some basic Code Snippets:

* How to write a collection sort 

```text
Collections.sort(letterList, (o1, o2) -> {
    String[] s1 = o1.split(" ");
    String[] s2 = o2.split(" ");
    int len1 = s1.length;
    int len2 = s2.length;
    for (int i = 1; i < Math.min(len1, len2); i++) {
        if (!s1[i].equals(s2[i])) {
            return s1[i].compareTo(s2[i]);
        }
    }
            return 0;
});
```

* 
