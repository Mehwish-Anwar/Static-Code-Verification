# 2. Code Review Report

| Line Number | Defect Type | Why It Is a Problem | Proposed Fix | Severity |
|:---:|---|---|---|:---:|
| 35 | Array Overflow | `spawnMonster()` inserts a monster without checking whether the array is full. This can cause out-of-bounds access. | Check `if (monsterCount >= MAX_MONSTERS) return;` before inserting a monster. | High |
| 41 | Logic Bug / Assignment | `if (monsters[i]->id = id)` uses `=` instead of `==`. It changes the monster's ID instead of comparing it. | Change it to `if (monsters[i]->id == id)`. | High |
| 48, 62, 80 | Null Pointer Dereference | `findMonster(id)` may return `nullptr`. Accessing `m->health` or `m->name` without checking the pointer can crash the program. | Check `if (m == nullptr)` before accessing the monster's members. | High |
| 49–50 | Underflow / Type Issue | `dmg` is unsigned. Subtracting a larger damage value from a smaller health value can cause underflow. Therefore, checking whether the result is less than zero will not work correctly. | Check `if (m->health <= dmg)` before subtraction, or use suitable signed integer types. | Medium |
| 58 | Off-by-One Error | The condition `i <= monsterCount` accesses an extra array position that may be invalid. | Change the loop condition to `i < monsterCount`. | High |
| 65 | Dangling Reference | Returning a reference to the local variable `label` is unsafe because the variable is destroyed when the function ends. | Return the string by value using `std::string`. | High |
| 70, 73 | Uninitialized Variable / Division by Zero | `double sum;` is not initialized. Also, dividing by `monsterCount` when it is zero causes a division-by-zero error. | Initialize with `double sum = 0.0;` and check that `monsterCount > 0` before dividing. | High |
| 81–82 | Use-After-Free | The statement `delete m;` destroys the object. Accessing `m->name` afterward uses freed memory and may crash the program. | Print the name before deleting the object and remove its pointer from the array. | High |
| 86 | Integer Division | Integer arithmetic may remove the fractional part of the result, causing inaccurate calculations. | Use `double` values or cast the calculation to `double` when fractional results are required. | Low |
| 92 | Missing Return Statement | The function `playerRank()` does not return a value when `score <= 100`, which can cause undefined behavior. | Add a suitable return statement for this condition. | Medium |
| 96, 102 | Mismatched Delete / Buffer Overflow Risk | Memory allocated using `new char[10]` requires `delete[]`. Also, `cin >> name` may overflow the buffer if the input is too long. | Use `std::string` instead of a character array, or use `delete[]` and safely limit the input length. | High |
| 113 | Memory Leak | The object `bonus` is created using `new Monster(...)` but is never deleted, causing a memory leak. | Delete the object when it is no longer needed or use `std::unique_ptr`. | Medium |
| 125 | Shallow Copy / Double Free | `Game copy = game;` copies the pointers instead of creating separate monster objects. Both objects may try to delete the same memory. | Implement a proper copy constructor and assignment operator, or disable copying. Smart pointers may also help. | High |


