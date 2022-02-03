# **VHDL Invariants**
<pre>
1. VHDL is NOT case sensitive
   - Dout <= A and B;
   - doUt <= a AnD B; 
2. VHDL is NOT sensitive to white space (spaces & tabs)
   - nQ <= In_a or In_b;
   - nQ  <=In_a or   In_b;
3. Comments begin with '__' (2 hyphens)
   - There is no block commenting
4. Use parenthesis to properly convey purpose of code
   - if x = '0' and y = '0' or z = '1' then
         blah; --some statement
   - if (((x = '0') and (y = '0')) or (z = '1')) then
         blah; --some statement
5. All statements end in a semicolon (;)
6. if, case, and loop statements
   - Every 'if' statement has a corresponding 'then' component
   - Each 'if' statement is terminated with an 'end if;'
   - An else if construct is 'elsif' in VHDL
   - Each 'case' sytatement is terminated with an 'end case;'
   - Each 'loop' statement has a correspondng 'end loop;'
</pre>
