```
O O O O O O O O
O O ■ ■ ■ ■ O O
O ■ ■ O O ■ ■ O
O ■ O O O O O O
O ■ O O ■ ■ ■ O
O ■ ■ O O ■ O O
O O ■ ■ ■ ■ O O
O O O O O O O O
```

# I heard you liked list comprehensions
```py
move = lambda b, p = max(
    (
        (
            ((b[r][c]==0)*sum(
                sum(1 for k in range(1,8)
                    if all(0<=r+dr*i<8 and 0<=c+dc*i<8 and b[r+dr*i][c+dc*i]==-p for i in range(1,k+1))
                    and 0<=r+dr*(k+1)<8 and 0<=c+dc*(k+1)<8 and b[r+dr*(k+1)][c+dc*(k+1)]==p
                )
                for dr,dc in [(-1,0),(1,0),(0,-1),(0,1),(-1,-1),(-1,1),(1,-1),(1,1)]
            )) + (((b[r][c]==0)*sum(
                sum(1 for k in range(1,8)
                    if all(0<=r+dr*i<8 and 0<=c+dc*i<8 and b[r+dr*i][c+dc*i]==-p for i in range(1,k+1))
                    and 0<=r+dr*(k+1)<8 and 0<=c+dc*(k+1)<8 and b[r+dr*(k+1)][c+dc*(k+1)]==p
                )
                for dr,dc in [(-1,0),(1,0),(0,-1),(0,1),(-1,-1),(-1,1),(1,-1),(1,1)]
            )) and (r in (0,7) and c in (0,7))), (r,c))
        for r in range(8) for c in range(8)
    ),
    default=(0,None), key=lambda x:x[0]
)[1]
```
