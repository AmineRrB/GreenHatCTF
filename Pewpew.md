  ## Challenge Description

-   Name: Pewpew
-   Points: 500
-   Description: "Find the hidden flag with arbitrary code execution using python's format string vulnerability."

## Tools and Techniques

-   Tools: no tools needed
-   Techniques:
- exploit python's format string vulnerability to execute arbitrary code

## Solution

1.  **Initial Approach**
    
    -   I downloaded an inspected the code, then noticed that our only input is the variable text.
    -   I noticed that the varibae text is used by the format methode with the arguments "self=self", which is vulnerable.
 
2.  **Detailed Solution**
    
    -   **Step 1**: Inspected the code and found the vulnerability.
        -   I analysed the code and found the vulnerability.
        -   The format methode was vulneable to dynamic placeholders.
    -   **Step 2**: Used hacktrick website to find the payload.
        -   searched for python's format string vulnerability in hacktrick.
        -   found the payload "{people_obj.__init__.__globals__[CONFIG][KEY]}".
    -   **Step 3**: Extracted the flag.
        -   modified the payload to "30}{self.pewpewpew.__globals__[secret]".
        -   the "30}" is to avoid the filter "{:#^" so it takes the whole payload and executes it.
        -   I netcated to the server then input the payload retrieve the flag. 

## Flag:
microCTF{p3wp3w!ng_f0rm4t_!5_d4ng3r0u5} 
