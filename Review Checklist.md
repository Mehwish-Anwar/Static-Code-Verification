# 1. Review Checklist

| No. | Category | Result | Defect / Issue Summary |
|:---:|---|:---:|---|
| 1 | Initialization | Issue | Uninitialized local variable (`double sum`) in `averageAttack()`. |
| 2 | Pointers | Issue | Null pointer dereferences (`m->...`), use-after-free (`delete m` followed by `m->name`), memory leaks (`bonus` and incorrect memory deallocation using `delete name`), and shallow-copy double-free (`Game copy = game;`). |
| 3 | Arrays / Buffers | Issue | Buffer overflow risk due to out-of-bounds array access (`monsters[monsterCount]`) when the array is full, incorrect loop bounds using `<=`, and unsafe `cin >> name` input that may overflow the buffer. |
| 4 | Loops | Issue | Off-by-one loop boundary error caused by `i <= monsterCount`, which may access an invalid array position. |
| 5 | Arithmetic | Issue | Division-by-zero risk if `monsterCount == 0`, and an unsigned arithmetic issue in `m->health - dmg < 0` because an unsigned result cannot be negative. |
| 6 | Control Flow | Issue | Missing return value in the non-void function `playerRank()` when `score <= 100`. |
| 7 | Function Calls / Returns | Issue | Dangling reference returned by `std::string& getMonsterLabel()`, which may refer to a local variable that is destroyed when the function ends. |
| 8 | Classes / OOP | Issue | Assignment operator (`=`) used instead of the equality operator (`==`) in `findMonster()`, and missing copy constructor and assignment operator implementation, which may cause shallow-copy and double-free problems. |

