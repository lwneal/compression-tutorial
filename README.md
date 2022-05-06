# compression-tutorial
Learn how compression works!

# Compressing Data

Sometimes we have a large amount of data. For example, the first one million numbers.

```
gromdar@gromdar2:~/gromdar$ seq 1000000 | tail
999991
999992
999993
999994
999995
999996
999997
999998
999999
1000000
```

```
gromdar@gromdar2:~/gromdar$ seq 1000000 | wc
1000000 1000000 6888896
```

Almost 7 megabytes! That's too big.


# Using gzip

If the data is too large, just use `gzip` to make it smaller.

```
gromdar@gromdar2:~/gromdar$ seq 1000000 | gzip - | wc
    297   27138 2129143
```

An improvement, but still quite large. So, we use `gzip` again.

    
```
gromdar@gromdar2:~/gromdar$ seq 1000000 | gzip - | gzip - | wc
    120     846   38364
```

Repeat as desired until the data is sufficiently small.

```
gromdar@gromdar2:~/gromdar$ seq 1000000 | gzip - | gzip - | gunzip | gunzip | tail
999991
999992
999993
999994
999995
999996
999997
999998
999999
1000000
```
