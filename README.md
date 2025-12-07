# Multi-Frequency GNSS Spoofing Raw Dataset

![License](https://img.shields.io/badge/license-MIT-blue) ![Data Size](https://img.shields.io/badge/data%20size-115MB-green) ![GNSS Bands](https://img.shields.io/badge/bands-L1%20%7C%20L5%20%7C%20L1%2BL5-orange)

## 📖 Overview

This dataset contains **GNSS Raw Measurements** collected from various Android smartphones and smartwatches under different spoofing attack scenarios. The data focuses on **L1, L5, and L1+L5 (L15)** frequency bands.

The logs were captured using the Android GNSS Logger and have been pre-processed to retain only the essential `Raw` measurement fields and device headers, making them lightweight and ideal for research in:
- **GNSS Spoofing Detection** (Signal Quality Monitoring, consistency checks).
- **Multi-frequency Integrity Analysis**.
- **Android Raw Measurements Analysis**.

---

## 📥 Download Dataset

The full dataset (**~115 MB**, `.zip`) is hosted in the **Releases** section of this repository.

> **[👉 Click here to download GNSS_Spoofing_Raw_Dataset_v1.0.zip](../../releases/latest)**

*Note: The repository itself only contains documentation and sample files. Please download the main data from the link above.*

---

## 🕒 Ground Truth & Spoofing Timelines

All devices within the same scenario folder were subjected to synchronized spoofing attacks. The table below provides the exact timestamps for the **start** and **end** of the spoofing signal injection.

**Reference Date:** 2025-07-30 

| Scenario Folder | Attack Type          | GPS TOW Interval (s) | UTC Time Interval (YYYY-MM-DD)         | Duration |
| :-------------- | :------------------- | :------------------- | :------------------------------------- | :------- |
| **st_L_15**     | L1 + L5 Simultaneous | `258028` - `258653`  | **2025-07-29 23:40:10** - **23:50:35** | ~10 min  |
| **st_L1**       | L1 Only              | `262228` - `262860`  | **2025-07-30 00:50:10** - **01:00:42** | ~10 min  |
| **st_L5**       | L5 Only (Phase 1)    | `265395` - `265490`  | **2025-07-30 01:42:57** - **01:44:32** | ~1.5 min |
| **st_L5**       | L5 Only (Phase 2)    | `266310` - `267054`  | **2025-07-30 01:58:12** - **02:10:36** | ~12 min  |
| **normal**      | Clean Data           | N/A                  | No Spoofing Injection                  | -        |

> **⚠️ Note:** The timestamp fields inside the log files (`utcTimeMillis`, `TimeNanos`) are based on the device's internal clock or decoded GNSS time. Please use the UTC times above as the ground truth reference.

---

## 📂 Directory Structure

The dataset follows a hierarchical structure: `Scenario` -> `Session_Timestamp` -> `Device_Model` -> `Log_File`.

```text
GNSS_Spoofing_Dataset/
├── st_L1/                          <-- Scenario: L1 Spoofing
│   └── 2025.07.30.08.40_2025.07.30.09.12/
│       ├── Google_pix6/            <-- Device: Google Pixel 6
│       │   └── gnss_log_2025_07_30_08_40_28.txt
│       ├── Huawei_Mate40/          <-- Device: Huawei Mate 40
│       │   └── gnss_log_2025_07_30_08_40_xx.txt
│       └── ...
├── st_L5/                          <-- Scenario: L5 Spoofing
│   └── ...
├── st_L_15/                        <-- Scenario: L1 + L5 Spoofing
│   └── ...
└── normal/                         <-- Clean Data (No attack)
    └── ...
```

---

## 📱 Devices Used

The dataset includes data from the following consumer-grade Android devices:

*   **Smartphones:**
    *   **Google Pixel 6**
    *   **Huawei Mate 40** 
    *   **XiaoMi MI8**
    *   **RedMi K60**
*   **Wearables:**
    *   **Google Pixel Watch**
    *   **Google Pixel Watch 2**

---

## 🛠 Data Format & Processing

The files are provided in standard **Android GNSS Logger Text Format**. To reduce file size and focus on signal analysis, we have processed the original logs.

**Retained Information:**

1.  **Header Comments (`# ...`):** Contains crucial device info (Hardware Model, Platform Version) and Column Definitions (`# Raw,...`).
2.  **Raw Measurements (`Raw`):** Contains Code Phase, Carrier Phase, Doppler, CN0, etc.

**Example content:**
```text
# Version: v3.0.6.3 Platform: 10 Manufacturer: HUAWEI Model: NOH-AN01
# ...
# Raw,utcTimeMillis,TimeNanos,LeapSecond,TimeUncertaintyNanos,FullBiasNanos,...
Raw,1753840212998,934580149375,18,0.0,-1437874496418804609,...
Raw,1753840212998,934580149375,18,0.0,-1437874496418804609,...
```

## 📜 Citation

This dataset is part of our research paper currently under review.  If you intend to use this dataset, please keep an eye on this repository for the updated citation information.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
