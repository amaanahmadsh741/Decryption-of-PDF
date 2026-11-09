
# PDF Decryption Using QPDF on Windows PowerShell

## 1. Objective

Install and configure QPDF on Windows 10 and use it to decrypt a password-protected PDF file through Windows PowerShell.

**Environment:**
- Operating System: Windows 10 (64-bit)
- Shell: Windows PowerShell
- Package Manager: Windows Package Manager (Winget)
- PDF Utility: QPDF 12.4.2
- Working Directory: "C:\Path\To\Your\PDF\Folder"

### Step-by-Step Installation Process

### Step 1: Open Windows PowerShell

1. Press `Win + X`.
2. Open Windows PowerShell or Windows Terminal.
3. Administrator access is generally not required for the following user-level commands.

### Step 2: Check Winget Installation

Execute:

```powershell
winget --version
```

Expected output:

```text
v1.29.380
```

The exact version may differ.

### Step 3: Search for QPDF

Execute:

```powershell
winget show --id QPDF.QPDF -e
```

This displays the package information.

Expected package details:

```text
Found QPDF [QPDF.QPDF]
Version: 12.4.2
Publisher: QPDF
```

### Step 4: Install QPDF

Execute:

```powershell
winget install --id QPDF.QPDF -e
```

Wait for the installation to complete.

### Step 5: Verify Installation

Check whether Winget recognizes the installed package:

```powershell
winget list --id QPDF.QPDF -e
```

Expected output:

```text
Name    Id        Version
qpdf    QPDF.QPDF 12.4.2
```

### Step 6: Locate the QPDF Executable

Actual installation location:

### Verify PATH Configuration

Close PowerShell and open a new window.

Execute:

```powershell
where.exe qpdf
```

Expected output:

```text
C:\Program Files\qpdf 12.4.2\bin\qpdf.exe
```

Now execute:

```powershell
qpdf --version
```

Expected output:

```text
qpdf version 12.4.2
```

### 7. Navigate to the Working Directory

The PDF files are stored in:

Correct:
```powershell
cd "C:\Path\To\Your\PDF\Folder"
```

### 8. Decrypt the Password-Protected PDF

## Command Syntax

```powershell
& "C:\Program Files\qpdf 12.4.2\bin\qpdf.exe" --password="YOUR_PASSWORD" --decrypt "C:\Path\To\Your\PDF\Folderinput.pdf" "C:\Path\To\Your\PDF\Folderoutput.pdf"
```
### Actual Example

```powershell
qpdf --password="YOUR_PASSWORD" --decrypt "input.pdf" "output.pdf"
```

Replace `YOUR_PASSWORD` with the actual PDF password.
Then it will convert the protected PDF to an Unprotected PDF
Check that the file is not password-protected 

**Command explanation:**

| Parameter | Purpose |
|---|---|
| `qpdf` | Runs the QPDF utility |
| `--password` | Supplies the PDF password |
| `--decrypt` | Removes encryption restrictions where permitted |
| `input.pdf` | Input PDF filename |
| `output.pdf` | Output PDF filename |

Only perform this operation on documents you own or are authorized to access.

## 8. Verify the Decrypted PDF
Review the output to verify the encryption status.

## 9. Common Errors and Solutions

| Error | Cause | Solution |
|---|---|---|
| `qpdf is not recognized` | QPDF directory missing from PATH | Configure PATH |
| `C:\Program is not recognized` | Path contains spaces | Use `&` and quotation marks |
| CMD syntax used in PowerShell | Use `cd "D:\folder"` |
| `ls is not recognized` in CMD | Linux/PowerShell command used in CMD | Use `dir` or open PowerShell |
| Incorrect password | Password does not match | Verify the PDF password |
| Output already exists | Existing output filename | Choose a different output filename |

## 10. Useful QPDF Commands

| Command | Description |
|---|---|
| `qpdf --version` | Displays QPDF version |
| `qpdf --help` | Displays help |

## 11. Final Workflow Summary

```text
Open Windows PowerShell
          |
          v
Check Winget Version
          |
          v
Find QPDF Package
          |
          v
Install QPDF Using Winget
          |
          v
Verify Installation
          |
          v
Locate qpdf.exe
          |
          v
Configure Windows PATH
          |
          v
Restart PowerShell
          |
          v
Verify qpdf --version
          |
          v
Navigate to PDF Directory
          |
          v
Execute QPDF Decryption Command
          |
          v
Verify Output PDF
          |
          v
Complete
```

## 12. Final Result

QPDF was installed successfully through Winget, its executable directory was configured in the Windows PATH environment variable, and the PDF decryption workflow was successfully tested using Windows PowerShell.

**Skills Practised:**
- Windows PowerShell navigation
- Winget package management
- Software installation
- Windows environment variables
- PATH configuration
- Executing programs with paths containing spaces
- PDF encryption and decryption
- Basic troubleshooting

**Official Documentation:**

- QPDF: https://qpdf.readthedocs.io/
- Winget: https://learn.microsoft.com/en-us/windows/package-manager/winget/
- PowerShell: https://learn.microsoft.com/en-us/powershell/
