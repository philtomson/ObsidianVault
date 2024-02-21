
Note from Hacker news:  https://news.ycombinator.com/item?id=38905182

"... and arrays that don't decay to pointers. (Which, in my opinion, is C's real million-dollar mistake, not null pointers.)"

Answered by mjburgess:

""That's seems fixable with a standard library, if you define,

```
    typedef struct { byte *data; u64 len; } array;
    typedef struct { byte *data; u64 len; u64 cap; } vec;

    typedef struct { byte *data; u64 len; } string;
```

etc.

Then developers will adhere to those apis, _so long as_, one's own array-struct decays to the above, so there can be standard library fns against the above, eg.,

```
    sort(array *a); 
```

etc.