# Python Ransomware Simulation & Deep Freeze Demo

🛡️ This repository demonstrates how to simulate a simple ransomware attack in Python and how Faronics Deep Freeze automatically restores encrypted files on reboot.
**For educational/testing purposes only — do *not* run on production or sensitive systems.**

---

## 🎥 Demo Video

Watch the full walkthrough here:
[https://youtu.be/rmlSk37btHA](https://youtu.be/rmlSk37btHA)

---

## 📆 Software & Tools Used

| Tool                              | Version / Notes                     |
| --------------------------------- | ----------------------------------- |
| Windows 10 VM                     | 21H2                                |
| Python                            | 3.8+                                |
| cryptography, watchdog, psutil    | Latest via `pip install`            |
| PyInstaller                       | Latest (optional, for bundling)     |
| Deep Freeze Standard / Enterprise | Latest (configure folder in Frozen) |
| Hypervisor                        | Hyper-V / VMware (optional)         |

---

## ⚙️ Project Structure

```
DigitalForensic-Python/
├── setup_dummy_files.py      # Generates dummy .txt/.jpg files
├── trojan.py                 # Main “ransomware” script
├── requirements.txt          # Python dependencies
├── README.md                 # This file
├── deepfreeze_setup.mp4      # video of deepfreeze installation
├── .gitignore                # mentions of files that not be the part of repo
├── LISENSE                   #lisense mit
└── python_ransomware_demo.mp4
```

---

## 🔧 Installation & Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/farman20ali/digital-forensic-deepfreeze.git
   cd digital-forensic-deepfreeze
   ```

2. **Create & activate a virtual environment**

   ```bash
   python -m venv venv
   venv\Scripts\activate           # Windows
   # or
   source venv/bin/activate        # macOS/Linux
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

   *Contents of `requirements.txt`*

   ```
   cryptography
   watchdog
   psutil
   ```

4. **(Optional) Bundle as a Windows executable**

   ```bash
   pip install pyinstaller
   pyinstaller --onefile --windowed trojan.py
   ```

   * Output: `dist/trojan.exe` — rename to `Invoice.pdf.exe` to mimic disguise.

---

## 🗂 Generating Dummy Files

Populate your Deep Freeze–protected folder:

```bash
python setup_dummy_files.py --target test_files --count 50
```

* `--target`: Path to your Deep Freeze–protected directory.
* `--count`: Number of dummy files (mix of `.txt` & `.jpg`).

---

## 🔒 Running the “Trojan”

1. **Ensure Deep Freeze is in “Frozen” mode** protecting `test_files`.

2. **Execute the ransomware script**:

   * **As a script**

     ```bash
     python trojan.py --path test_files
     ```
   * **As an executable**

     ```bash
     dist\Invoice.pdf.exe --path test_files
     ```

3. **Observe:** All files in `test_files` will be renamed with a `.enc` extension.

4. **Reboot** the VM → Deep Freeze restores the entire folder to its pre-attack state.

---

## 📺 Video Demos
* **Deep Freeze Setup & Restore**

  [https://www.youtube.com/watch?v=4ytj5k5IwjQ](https://youtu.be/KnLWQDQDQmA)
  
* **Python Ransomware Simulation**
  [https://youtu.be/rmlSk37btHA](https://youtu.be/rmlSk37btHA)

*(You can download local copies into from repo for offline demos.)*

---

> ⚠️ **Disclaimer:**
> This code is strictly for controlled, educational environments. Never run ransomware simulations on production data or without explicit authorization.

---

## 🙌 Contributions

Pull requests welcome! Feel free to improve the simulation logic, add new defense integrations, or enhance documentation.
