## gdb
1. 观察某个结构体中成员的值，变成某一个值时中断 `watch (z > 28)`
2. `tbreak`, `util`
   >Execute until the program reaches a source line greater than the current [one].  

   >You could set a temporary breakpoint at the future code and use continue; however, this is exactly the situation that until was meant to address.  

   >**In fact**, what until really does is execute until it reaches a machine instruction that has a higher memory address than the current one, rather than until it reaches a larger line number in the source code.  

   >`until 17`, `until swap`, `until swapflaw.c:17`, `until swapflaw.c:swap`

3. help breakpoints
4. `condition 1 num_y==1`, makes that breakpoint conditional: GDB will pause execution of
the program at breakpoint 1 only when the condition `num_y==1 `holds. We could have **combined the break and condition** commands into a single step by using break if as follows: `break 30 if num_y==1`
5. **DO not exit GDB or EDITOR.**
   >Because we wisely chose to stay in the GDB
session, rather than exiting GDB after discovering and fixing the first bug, the breakpoint and its condition, which we set earlier, are still in effect now.  

   >Likewise, you should not keep exiting and restarting your text editor
during your debugging session, which would also be a distraction and a
waste of time. 
6. **Startup Files**.
   >GDB’s startup files are named **.gdbinit** by default.  
   You can have one in your **home directory for general purposes** and another in the **directory containing a particular project** for purposes specific to that project

   >`gdb -command=z x`  
   > run GDB on the executable file x, first reading in commands
from the file z
7. `delete breakpoint_list`, `delete`, `clear`, `clear function`, `clear filename:function`, `clear line_number`, `clear filename:line_number`
   > The delete command is used to delete breakpoints based on their identifier, and the clear
command is used to delete breakpoints using the same syntax you use to create breakpoints
8. `break main`, `break 35`, `break source/bed.c:35`, `break bed.c:parseArguments`, `break *address`
   >Using break function will set a breakpoint at all
functions with the same name.
9. The location at which GDB actually sets a breakpoint may be different
from where you requested it to be placed.
   > Recall that GDB actually works with machine language instructions, but with the magic of an enhanced symbol table, GDB gives the illusion of working with source code
lines. 
10. `list swap`
11. `disable breakpoint_list`, `enable breakpoint_list`, `enable once breakpoint-list`
12. `continue n`
13. `break break-args if (condition)`
    > Conditional breaking is extremely useful, particularly in loop constructs in which something bad happens at a particular value of the index variable.

    > Conditional breaking is also extremely flexible. Pretty much any expression you can use in a valid C conditional statement.   

    > `break 180 if string==NULL && i < 0`  
    `break test.c:34 if (x & y) == 1`  
    `break myfunc if i % (j + 3) != 0`  
    `break test.c:myfunc if ! check_variable_sanity(i)`  
    `break 44 if strlen(mystring) == 0`  
14. `cond 3 i == 3`, `cond 3`
    > if you have set breakpoint 3 as unconditional but now wish to add the condition i == 3: `cond 3 i == 3`  
    If you later want to remove the condition but keep the breakpoint, simply type: `cond 3`