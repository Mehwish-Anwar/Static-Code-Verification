1. Review Checklist

| No. | Category | Result | Defect / Issue Summary |
|---|---|---|---|
| 1 | Initialization | Issue | Uninitialized local variable (`double sum`) in `averageAttack()`. |
| 2 | Pointers | Issue | Null pointer dereferences (`m->...`), use-after-free (`delete m` followed by `m->name`), memory leaks (`bonus`, `delete name`), and shallow-copy double-free (`Game copy = game;`). |
| 3 | Arrays / Buffers | Issue | Buffer overflow due to out-of-bounds array access (`monsters[monsterCount]` when the count reaches 5 or incorrect loop bounds using `<=`), and unsafe `cin >> name` causing buffer overflow. |
| 4 | Loops | Issue | Off-by-one loop boundary error (`i <= monsterCount`). |
| 5 | Arithmetic | Issue | Division-by-zero risk if `monsterCount == 0`, and signed/unsigned comparison bug in `m->health - dmg < 0` because an unsigned value cannot be negative. |
| 6 | Control Flow | Issue | Missing return value in the non-void function `playerRank()` when `score <= 100`. |
| 7 | Function Calls / Returns | Issue | Dangling reference returned by the function `std::string& getMonsterLabel()`. |
| 8 | Classes / OOP | Issue | Assignment operator used instead of equality comparison in `findMonster()` (`= id` instead of `== id`), and missing copy constructor and Rule of Three implementation. |
