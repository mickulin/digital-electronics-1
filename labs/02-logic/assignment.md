# Lab 2: Petr Mička

### 2-bit comparator

1. Karnaugh maps for other two functions:

   Greater than:

  |B1B0/A1A0| **00** | **01** | **11** | **10** |
  | :-:    | :-:    | :-:    | :-:    | :-:    |
  | **00** |   0    |   0    |   0    |   0    |
  | **01** |   1    |   0    |   0    |   0    |
  | **11** |   1    |   1    |   0    |   1    |
  | **10** |   1    |   1    |   0    |   0    |
  
   Less than:
   
  |B1B0/A1A0| **00** | **01** | **11** | **10** |
  | :-:    | :-:    | :-:    | :-:    | :-:    |
  | **00** |   0    |   1    |   1    |   1    |
  | **01** |   0    |   0    |   1    |   1    |
  | **11** |   0    |   0    |   0    |   1    |
  | **10** |   0    |   0    |   1    |   0    |
   

2. Equations of simplified SoP (Sum of the Products) form of the "greater than" function and simplified PoS (Product of the Sums) form of the "less than" function.

   ![Logic functions](images/vzorce.PNG)

### 4-bit comparator

1. Listing of VHDL stimulus process from testbench file (`testbench.vhd`) with at least one assert (use BCD codes of your student ID digits as input combinations). Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

   Last two digits of my student ID: **16**

```vhdl
   p_stimulus : process
    begin
        -- Report a note at the beginning of stimulus process
        report "Stimulus process started" severity note;

        -- First test case ...
        s_b <= "0001"; s_a <= "0010"; wait for 100 ns;
        
        -- ... and its expected outputs
        assert ((s_B_greater_A = '0') and
                (s_B_equals_A  = '0') and
                (s_B_less_A    = '1'))
        -- If false, then report an error
        -- If true, then do not report anything
        report "Input combination 0001, 0010 FAILED" severity error;
		

        -- WRITE OTHER TEST CASES HERE
		s_b <= "0111"; s_a <= "0111"; wait for 100 ns;
        
        -- ... and its expected outputs
        assert ((s_B_greater_A = '0') and
                (s_B_equals_A  = '1') and
                (s_B_less_A    = '0'))
        -- If false, then report an error
        -- If true, then do not report anything
        report "Input combination 0111, 0111 FAILED" severity error;
        
        
        s_b <= "0111"; s_a <= "0101"; wait for 100 ns;
        
        -- ... and its expected outputs
        assert ((s_B_greater_A = '1') and
                (s_B_equals_A  = '0') and
                (s_B_less_A    = '0'))
        -- If false, then report an error
        -- If true, then do not report anything
        report "Input combination 0111, 0111 FAILED" severity error;


        -- Report a note at the end of stimulus process
        report "Stimulus process finished" severity note;
        wait; -- Data generation process is suspended forever
    end process p_stimulus;
```

2. Text console screenshot during your simulation, including reports.

   ![your figure](images/log.PNG)

3. Link to your public EDA Playground example:

   [https://www.edaplayground.com/...](https://www.edaplayground.com/x/uvZ8)
