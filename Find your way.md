## Challenge Description

-   Name: Find your way
-   Points: 500
-   Description: "Find the hidden flag using Server-Side Template Injection."

## Tools and Techniques

-   Tools: Burp Suite(not mandatory)
-   Techniques:
- Server-Side Template Injection
- using get methode parameters

## Solution

1.  **Initial Approach**
    
    -   I saw the "?age" on the inicial page.
    -   I added the age parameter with the values of 23 and it gave me the message.
    -   I knew it has replaced my values in a field somewhere, so its a RCE.
 
2.  **Detailed Solution**
    
    -   **Step 1**: Used Burp Suite to intercept the login request.
        -   added the age parameter with 23 as values.
        -   noticed the python process in the http response header.
    -   **Step 2**: Used hacktrick website to find the exploit.
        -   searched for python server side injection in hacktrick.
        -   found the SSTI section.
        -   found the python payload.
    -   **Step 3**: Extracted the flag.
        -   used the tornado payload , it triggered an error ,i knew the server executed it but failed.
        -   used the jinja2 payload "{{ self._TemplateReference__context.joiner.__init__.__globals__.os.popen('id').read() }}", it gave "uid=0(root) gid=0(root) groups=0(root)".
        -   executed "ls -l" to locate the flag then "cat flag.txt" to show it

## Flag:
"microCTF{I_D0nT_W4nna_Y0uR_4g3_4nYm0r3}"
