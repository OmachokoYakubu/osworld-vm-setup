# Ubuntu VM Setup & Environment Preparation
## Technical Assessment Report

**Submitted by:** Omachoko Yakubu  
**Date:** November 16, 2025  
**Assessment:** OSWorld CUA SFT - Ubuntu VM Setup & LibreOffice Calc Task

---

## 1. Introduction

This report documents the complete process of setting up a Ubuntu 22.04 virtual machine environment for OSWorld automation and UI-interaction workflows. The assessment involved installing and configuring VMware, creating a virtual machine with specific hardware requirements, installing Ubuntu Desktop, configuring display settings to maintain a consistent 1920×1080 resolution, and completing a data cleaning task using LibreOffice Calc.

The primary goal of this assessment was to demonstrate practical system administration skills, attention to detail in following technical specifications, and the ability to work with spreadsheet applications for data transformation tasks. Throughout this process, I maintained comprehensive documentation through screenshots at each major phase to verify the workflow and ensure reproducibility.

---

## 2. Host Hardware Verification

Before beginning the VM setup, I verified that my host machine meets the mandatory minimum requirements for running VMware and Ubuntu virtualization workloads.

### Hardware Specifications:
- **RAM:** 16 GB (meets the mandatory 16GB minimum requirement)
- **CPU:** Multi-core processor with virtualization support enabled
- **Available Disk Space:** Sufficient space for VM allocation (40GB+ available)
- **Virtualization Support:** Intel VT-x / AMD-V enabled and functional
- **GPU:** Capable of rendering VMware UI and Ubuntu desktop environment

### Verification Process:
I ran the appropriate system commands to gather hardware information and confirmed that all specifications meet or exceed the minimum requirements. The most critical requirement—16GB of RAM—was verified and confirmed. This ensures the VM will run smoothly without freezing, lagging, or producing invalid automation trajectories.

**Screenshot Reference:** `host_hardware_specs.png`

---

## 3. VMware Installation

I downloaded and installed VMware Workstation Player to serve as the hypervisor for running the Ubuntu virtual machine. The installation process was straightforward and completed without any issues.

### Installation Steps:
1. Downloaded VMware Workstation Player from the official VMware website
2. Ran the installer with administrator privileges
3. Accepted the license agreement and followed the installation wizard
4. Completed the installation and restarted the system as prompted
5. Launched VMware for the first time to verify successful installation

The VMware interface loaded correctly, confirming that the installation was successful and the software was ready for VM creation.

**Screenshot References:**
- Installation window: `vmware_install_window.png`
- VMware home screen: `vmware_home.png`
- Version information: `vmware_version.png`

---

## 4. Ubuntu ISO Download

I downloaded the Ubuntu 22.04 LTS Desktop ISO image from the official Ubuntu releases website. Ubuntu 22.04 LTS (Long Term Support) was chosen as specified in the assessment requirements.

### Download Details:
- **Source:** https://releases.ubuntu.com/22.04/
- **Version:** Ubuntu 22.04.5 LTS
- **Architecture:** 64-bit (amd64)
- **File Size:** Approximately 4.5 GB

The ISO file was downloaded to my local system and verified to ensure integrity before proceeding with VM creation.

**Screenshot Reference:** `ubuntu_iso_download.png`

---

## 5. VM Creation

I created a new virtual machine in VMware with the specifications required for optimal Ubuntu desktop performance and OSWorld automation tasks.

### VM Configuration:
- **VM Name:** Ubuntu 64-bit
- **Operating System:** Ubuntu 22.04 (64-bit)
- **RAM:** 8192 MB (8 GB)
- **CPU Cores:** 2
- **Disk Size:** 40 GB
- **Disk Type:** Single file, dynamically allocated
- **3D Acceleration:** Enabled
- **ISO Path:** /home/replica/vmware/Ubuntu 64-bit

### Configuration Process:
1. Opened VMware and selected "Create a New Virtual Machine"
2. Chose "Installer disc image file (iso)" and browsed to the Ubuntu ISO
3. Configured the virtual machine name and storage location
4. Allocated 8GB of RAM to ensure smooth operation
5. Assigned 2 processor cores for adequate performance
6. Created a 40GB virtual hard disk
7. Customized hardware settings to enable 3D graphics acceleration
8. Reviewed the configuration summary before completing creation

The VM was successfully created with all specifications meeting the assessment requirements. The configuration details were saved to `VM_Config.txt` for reference.

**Screenshot Reference:** `VM_Config.png`

---

## 6. Ubuntu Installation

With the virtual machine created, I proceeded to install Ubuntu 22.04 Desktop following the standard installation procedure.

### Installation Process:
1. Powered on the virtual machine, which booted from the Ubuntu ISO
2. Selected "Install Ubuntu" from the boot menu
3. Chose English as the installation language
4. Selected keyboard layout (English US)
5. Chose "Normal installation" with the option to download updates during installation
6. Selected "Erase disk and install Ubuntu" (this only affects the virtual disk)
7. Configured timezone settings
8. Created user account with username and password
9. Waited for the installation to complete (approximately 20-30 minutes)
10. Restarted the VM as prompted after installation

The installation completed successfully without any errors. After reboot, I was able to log in to the Ubuntu desktop environment for the first time.

**Screenshot References:**
- Installation start screen: `ubuntu_install_start.png`
- Keyboard selection: `ubuntu_install_keyboard.png`
- Installation progress: `ubuntu_install_progress.png`
- First login to desktop: `ubuntu_first_login.png`

---

## 7. Ubuntu Display Resolution Configuration

After logging into Ubuntu, I configured the display resolution to 1920×1080 (Full HD) as required for consistent UI automation workflows.

### Resolution Configuration Steps:
1. Opened the Settings application from the application menu
2. Navigated to Settings → Displays
3. Changed the resolution from the default to 1920 × 1080 (16:9)
4. Set the display scale to 100%
5. Applied the changes and confirmed when prompted
6. Verified that the desktop displayed correctly at the new resolution

The display settings were successfully applied, and the Ubuntu desktop rendered properly at 1920×1080 resolution with 100% scaling.

**Screenshot References:**
- Display settings dialog: `resolution_settings.png`
- Full desktop at 1920×1080: `resolution_full_desktop.png`

---

## 8. VMware Resolution Locking

To ensure the VM maintains a consistent 1920×1080 resolution regardless of the VMware window size, I configured VMware's display settings to lock the resolution. This is critical for UI automation as it prevents the guest OS from changing resolution dynamically.

### Resolution Locking Steps:
1. Shut down the Ubuntu VM temporarily
2. Opened VM → Settings → Display in VMware
3. Disabled the following options:
   - Autofit Guest
   - Autofit Window
   - Stretch Guest
   - Automatically Adjust User Interface Size
4. Unchecked "Use host setting for monitors"
5. Enabled "Specify monitor settings"
6. Set custom resolution to 1920 × 1080
7. Saved the settings and restarted the VM

### Verification:
After restarting, I verified that:
- Ubuntu maintained 1920×1080 resolution
- Resizing the VMware window did not change the guest resolution
- Scrollbars appeared when the window was smaller than the resolution
- The viewport remained at Full HD regardless of window size

This configuration ensures display consistency essential for correct trajectory generation in automation tasks.

**Screenshot References:**
- VMware display settings: `vmware_display_settings .png`
- Ubuntu with locked FHD resolution: `ubuntu_fhd_locked.png`
- Resized VMware window with fixed resolution: `fhd_lock_resized_window.png`

---

## 9. System Verification

To validate the Ubuntu installation and configuration, I ran several system verification commands in the terminal and documented the output.

### Commands Executed:
1. `lsb_release -a` - Verified Ubuntu version and distribution information
2. `uname -a` - Checked kernel version and system architecture
3. `df -h` - Verified disk space allocation and usage
4. `echo $XDG_SESSION_TYPE` - Confirmed the display server type (Wayland)

### Results:
- **OS:** Ubuntu 22.04.5 LTS (Jammy)
- **Kernel:** 6.8.0-87-generic
- **Architecture:** x86_64
- **Disk Usage:** 12GB used out of 39GB available on root partition
- **Session Type:** Wayland
- **Boot Partition:** 512MB with minimal usage

All verification commands executed successfully, confirming that Ubuntu is properly installed and configured. The output was saved to `Verification_File.txt` for reference.

**Screenshot Reference:** `verification_terminal.png`

---

## 10. LibreOffice Calc Assessment Task Process

### Task Overview:
I was provided with a messy CSV file named `customer_orders_2023.csv` containing customer order data with various data quality issues. The task required:
- Removing rows with invalid email formats
- Standardizing phone numbers to (XXX) XXX-XXXX format
- Converting state abbreviations to full state names
- Saving the cleaned data as `orders_cleaned.csv`

### Original Data Analysis:
The original dataset contained 11 rows (including header) with the following issues:
- **Invalid emails:** 4 rows had email addresses without proper domain extensions (e.g., "jane.smith@example", "charlie@example")
- **Inconsistent phone formats:** Mix of plain digits, parentheses, hyphens, and dots
- **State abbreviations:** Two-letter codes (CA, NY, TX, FL, WA, OR, NV, UT, AZ, CO)

### Step-by-Step Process:

#### Step 1: Open CSV in LibreOffice Calc
I navigated to the file location and opened `customer_orders_2023.csv` in LibreOffice Calc. The data loaded correctly, showing all columns: Name, Email, Phone, and State.

**Screenshot:** `01_csv_loaded.png`

#### Step 2: Identify Invalid Email Formats
I inspected the Email column and identified rows where email addresses were missing proper domain extensions. I highlighted these rows for removal:
- Jane Smith: jane.smith@example
- Charlie Davis: charlie@example
- Grace Hill: ghill@example
- Ivy Jones: ivy.jones@example

**Screenshot:** `02_invalid_emails_highlighted.png`

#### Step 3: Remove Invalid Email Rows
I selected and deleted all rows containing invalid email addresses. This reduced the dataset from 10 data rows to 6 valid customer records.

**Screenshot:** `03_invalid_emails_removed.png`

#### Step 4: Standardize Phone Numbers
I transformed all phone numbers to the (XXX) XXX-XXXX format:
- Before: Mixed formats like "1234567890", "555-123-4567", "999.888.7777"
- After: Consistent format like "(123) 456-7890", "(555) 123-4567", "(999) 888-7777"

I used LibreOffice Calc's find-and-replace functionality combined with manual formatting to achieve consistent formatting across all phone numbers.

**Screenshots:** 
- Before standardization: `04_phone_numbers_before_standardization.png`
- After standardization: `04_phone_numbers_standardized.png`

#### Step 5: Convert State Abbreviations
I replaced all two-letter state abbreviations with their full state names:
- CA → California
- TX → Texas
- FL → Florida
- OR → Oregon
- NV → Nevada
- AZ → Arizona

**Screenshot:** `05_state_names_converted.png`

#### Step 6: Final Review
I reviewed the complete dataset to ensure all transformations were correctly applied:
- All emails are valid (contain proper domain)
- All phone numbers follow (XXX) XXX-XXXX format
- All states are spelled out in full
- No data corruption or missing values

**Screenshot:** `06_final_review.png`

#### Step 7: Save Cleaned File
I saved the cleaned dataset as `orders_cleaned.csv` using File → Save As, ensuring the file format remained as CSV (Comma-Separated Values).

**Screenshot:** `07_saved_orders_cleaned.png`

#### Step 8: Verification
To verify the cleaning process, I reopened `orders_cleaned.csv` in LibreOffice Calc and confirmed that all transformations persisted correctly after saving.

**Screenshot:** `08_verification_loaded.png`

### Results Summary:
- **Original rows:** 10 data rows
- **Cleaned rows:** 6 data rows (4 invalid rows removed)
- **Phone format:** 100% standardized to (XXX) XXX-XXXX
- **State names:** 100% converted to full names
- **Data integrity:** Maintained throughout the process

All completion criteria were met successfully.

---

## 11. Troubleshooting & Issues Faced

Throughout the assessment, I encountered a few minor challenges that were resolved successfully:

### Issue 1: VMware Display Settings
**Problem:** Initially, when I resized the VMware window, the Ubuntu guest resolution would change dynamically, which would affect UI automation consistency.

**Solution:** I configured VMware's display settings to disable auto-fit and auto-resize options, then specified a custom monitor resolution of 1920×1080. This locked the guest resolution regardless of host window size.

### Issue 2: Phone Number Formatting in LibreOffice Calc
**Problem:** The phone numbers in the original dataset had multiple inconsistent formats (plain digits, dots, hyphens, parentheses in different positions).

**Solution:** I used a combination of Find & Replace and manual editing to standardize all phone numbers. For entries that were just digits, I manually inserted parentheses around the first three digits and a space and hyphen for the remaining digits to achieve the (XXX) XXX-XXXX format.

### Issue 3: State Name Conversion
**Problem:** Manually typing full state names for each row would be time-consuming and error-prone.

**Solution:** I used LibreOffice Calc's Find & Replace feature (Ctrl+H) to replace each state abbreviation with its full name. I did this one state at a time to ensure accuracy (e.g., Find "CA", Replace with "California").

### General Observations:
- The VM performed smoothly with 8GB RAM allocation
- Ubuntu 22.04 was stable throughout the entire assessment
- LibreOffice Calc handled the CSV files without any formatting issues
- Screenshot capture worked reliably using the built-in screenshot tool

No critical issues prevented completion of any assessment requirements.

---

## 12. Time Spent

### Time Breakdown:

| Task | Time (hours) |
|------|--------------|
| VMware Setup | 0.5 |
| Ubuntu Installation | 1.5 |
| Resolution Configuration | 0.5 |
| System Verification | 0.5 |
| LibreOffice Task | 0.5 |

**Total Time:** Approximately 3.5 hours

The Ubuntu installation phase took the most time due to the ISO download and the actual OS installation process. The LibreOffice data cleaning task required careful attention to detail for identifying invalid emails, standardizing phone formats, and converting state names while maintaining data integrity.

---

## Conclusion

This assessment successfully demonstrated my ability to:
- Set up and configure virtualization environments
- Install and configure Linux operating systems
- Manage display settings for consistent UI environments
- Perform data validation and transformation tasks
- Document technical processes thoroughly with screenshots
- Follow detailed specifications and requirements accurately

All mandatory requirements were met:
- ✓ Host hardware meets 16GB RAM minimum
- ✓ VMware installed and configured correctly
- ✓ Ubuntu 22.04 installed successfully
- ✓ VM runs reliably at fixed 1920×1080 resolution
- ✓ Display settings configured and locked properly
- ✓ System verification commands executed and documented
- ✓ LibreOffice Calc task completed with all required transformations
- ✓ All screenshots provided and properly organized
- ✓ Comprehensive report completed

The environment is now ready for OSWorld automation and UI-interaction workflows with consistent display settings that ensure accurate trajectory generation.

---

**End of Report**
