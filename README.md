
# Decryption-of-PDF
Decrypting a PDF or Removing a Password from a PDF using Windows PowerShell
To remove a password from a PDF offline in Windows 10 using the Command Prompt (CMD), you can use open-source command-line tools like QPDF, provided you already know the password.

Method 1: Using QPDF

1. Download QPDF: Get the Windows binaries of QPDF from GitHub or SourceForge, extract the ZIP folder, and note the path to the bin folder (which contains qpdf.exe).

2. Open Command Prompt: Press Win + X and Select Windows PowerShell.
3. Navigate to your folder: Change the directory to the folder where your PDF file is saved.
   
4. Step 1: Check whether qpdf is installed
where qpdf
If it says INFO: Could not find files, install qpdf.

Step 2: Install using Windows Package Manager
If winget is available, run:
winget install --id QPDF.QPDF -e

Step 3: Close and reopen CMD, then verify:
qpdf --version

5. Check your system
Run these three commands in CMD and share the output:
winget --version
where qpdf
dir

Step 5. Verify installation
Close PowerShell and open a new PowerShell window.

Run:
qpdf --version

Expected output:
qpdf version 12.x.x

The exact version may differ.

Step 6. Also check where Windows finds QPDF:
where.exe qpdf

This should display the executable's location.
Your output shows:
C:\Program Files\qpdf 12.4.2\bin\qpdf.exe
This is your QPDF executable.

Step 7. Decrypt your PDF
Once Step 1 works, execute:
& "C:\Program Files\qpdf 12.4.2\bin\qpdf.exe" --password="YOUR_PASSWORD" --decrypt "C:\Path\To\Your\PDF\Folder\input.pdf" "C:\Path\To\Your\PDF\Folder\output.pdf"

Replace YOUR_PASSWORD with your PDF password.

Then it will convert the protected PDF to an Unprotected PDF
