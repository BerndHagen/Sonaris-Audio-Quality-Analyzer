<p align="center">
  <img src="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/sonaris-logo.png" alt="Sonaris Logo" width="128" />
</p>
<h1 align="center">Sonaris - Audio Quality Analyzer</h1>
<p align="center">
  <b>Analyze and grade audio quality across entire music libraries.</b><br>
  <b>Spectrum analysis, stereo correlation, clipping detection, and detailed reporting.</b>
</p>
<p align="center">
  <a href="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/releases"><img src="https://img.shields.io/github/v/release/BerndHagen/Sonaris-Audio-Quality-Analyzer?include_prereleases&style=flat-square&color=CD853F" alt="Latest Release"></a>&nbsp;&nbsp;<a href="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-Freeware-green?style=flat-square" alt="License"></a>&nbsp;&nbsp;<a href="https://dotnet.microsoft.com/download/dotnet/10.0/runtime"><img src="https://img.shields.io/badge/.NET-10.0-512BD4?style=flat-square" alt=".NET Version"></a>&nbsp;&nbsp;<img src="https://img.shields.io/badge/Platform-Windows-0078D6?style=flat-square" alt="Platform">&nbsp;&nbsp;<img src="https://img.shields.io/badge/Architecture-x64-lightgrey?style=flat-square" alt="Architecture">&nbsp;&nbsp;<img src="https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square" alt="Status">&nbsp;&nbsp;<a href="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/issues"><img src="https://img.shields.io/github/issues/BerndHagen/Sonaris-Audio-Quality-Analyzer?style=flat-square&color=orange" alt="Open Issues"></a>
</p>

**Sonaris** is a professional audio quality analyzer that scans and grades music libraries, production archives, masters, and distribution catalogs. It uses FFmpeg-powered spectral analysis to measure true frequency content per track, compares measured results against codec/bitrate expectations, and assigns quality grades from S (lossless/full-bandwidth) through F (severely degraded). The application supports batch scanning with configurable sampling, parallel analysis workers, stereo correlation, clipping detection, mastering quality assessment, upsampling/transcoding detection, and optional platform-aware grading profiles. Results can be exported as TXT, CSV, or JSON, and copied to clipboard.

### **Key Features**

- **Audio Quality Grading:** Assigns S through F grades based on measured spectral cutoff frequency, with clear thresholds for each tier.
- **Spectrum Analysis:** FFT-based frequency analysis with cascaded highpass filter probing to determine the true content cutoff of each track.
- **Multi-Window Analysis:** Analyzes both the beginning and midpoint of each track for more accurate cutoff detection across varying intros and outros.
- **Stereo Correlation:** Measures left/right channel correlation to identify mono content, true stereo, and phase issues.
- **Clipping Detection:** Detects digital clipping by counting samples at 0 dBFS and measuring inter-sample true peak levels.
- **Mastering Quality:** Evaluates mastering characteristics using integrated LUFS loudness (EBU R128), loudness range, dynamic range, and true peak headroom.
- **Upsampling Detection:** Identifies lossy audio falsely stored in lossless containers by comparing measured spectral content against claimed codec and bitrate.
- **Source-Profile Context (Optional):** Applies source-aware grading context only when relevant; this is an optional classification aid and not the core analysis mode.
- **Batch Scanning:** Analyze entire music libraries with configurable samples per folder, parallel workers, and per-file timeout settings.
- **Live Scan Progress:** Real-time grade distribution visualization and file-by-file progress during active scans.
- **Export Reports:** Export results as CSV, JSON, formatted text reports, or copy to clipboard.
- **Scan History:** Browse and review previous scan results with grade breakdowns and timestamps.
- **Track Classification:** Automatically identifies and excludes short sound effects and jingles from folder-level grading.
- **Cloud Settings Sync:** Sync analysis settings and scan history to the cloud via [Arctisoft Hub](https://github.com/BerndHagen/Arctisoft-Studio-Hub), keeping your configuration consistent across devices.

### **Supported Audio Formats**

Sonaris supports a wide range of audio formats for analysis:

- **Lossy Formats:** `MP3`, `AAC`, `M4A`, `OGG`, `OPUS`, `WMA`, `MPC`
- **Lossless Formats:** `FLAC`, `WAV`, `AIFF`, `APE`, `TTA`, `WV`

> **Format handling note:** Folder scans, drag-and-drop, and file picker all support the formats above.

> **Note:** Sonaris requires FFmpeg and ffprobe for audio analysis. On first launch, the application automatically downloads and installs these tools to a shared tools directory. No manual setup is required.

## **Table of Contents**

1. [System Requirements](#system-requirements)
   - [Minimum Requirements](#minimum-requirements)
   - [Recommended Requirements](#recommended-requirements)
2. [Third-Party Components](#third-party-components)
3. [Professional Workflows](#professional-workflows)
4. [Installation](#installation)
5. [Getting Started Guide](#getting-started-guide)
   - [Step 1: Select Files or Folders](#step-1-select-files-or-folders)
   - [Step 2: Review Scan Results](#step-2-review-scan-results)
   - [Step 3: Export or Browse History](#step-3-export-or-browse-history)
6. [Quality Grading System](#quality-grading-system)
   - [Absolute Grades](#absolute-grades)
  - [Source-Profile Relative Grades](#source-profile-relative-grades)
7. [Mastering Quality Assessment](#mastering-quality-assessment)
8. [Analysis Features](#analysis-features)
   - [Spectrum Analysis](#spectrum-analysis)
   - [Stereo Correlation](#stereo-correlation)
   - [Clipping Detection](#clipping-detection)
   - [Upsampling Detection](#upsampling-detection)
   - [Track Classification](#track-classification)
9. [Source Profile Detection (Optional)](#source-profile-detection-optional)
10. [Export Options](#export-options)
   - [CSV Export](#csv-export)
   - [JSON Export](#json-export)
   - [Text Report](#text-report)
   - [Copy to Clipboard](#copy-to-clipboard)
11. [Scan History](#scan-history)
12. [Settings](#settings)
    - [Analysis Settings](#analysis-settings)
    - [Advanced Analysis](#advanced-analysis)
    - [Export Settings](#export-settings)
13. [Cloud Settings Sync](#cloud-settings-sync)
14. [Keyboard Shortcuts](#keyboard-shortcuts)
15. [Copyright](#copyright)
16. [Screenshots](#screenshots)

## **System Requirements**

### **Minimum Requirements**
- **Operating System:** Windows 10 (64-bit) version 1809 or later
- **Processor:** Dual-core processor at 1.5 GHz
- **RAM:** 4 GB
- **Storage:** 500 MB of free disk space
- **Software:** .NET 10.0 Runtime ([Download](https://dotnet.microsoft.com/download/dotnet/10.0/runtime)) - **Not required as application is self-contained**

### **Recommended Requirements**
- **Operating System:** Windows 10/11 (64-bit) version 21H2 or later
- **Processor:** Quad-core processor at 2.0 GHz or higher
- **RAM:** 8 GB or higher
- **Storage:** 1 GB of free disk space on SSD
- **Software:** .NET 10.0 Runtime ([Download](https://dotnet.microsoft.com/download/dotnet/10.0/runtime)) - **Not required as application is self-contained**

**Note:** Sonaris is designed exclusively for Windows. Linux and macOS are not supported. The .NET 10.0 Runtime is bundled directly in the installer, allowing Sonaris to start immediately without requiring separate installation. FFmpeg and ffprobe are downloaded automatically on first launch.

## **Third-Party Components**

Sonaris is built with a minimal and transparent dependency footprint.

- **FFmpeg / ffprobe:** Core audio decoding, metadata extraction, loudness and signal analysis primitives.
- **Newtonsoft.Json (13.0.4):** JSON serialization for settings and data persistence.
- **WPF (.NET 10):** Native Windows desktop UI framework for rendering and interaction.

All grading and analysis logic (cutoff detection, grading rules, upsampling checks, source-profile context, track classification, and report generation) is implemented in Sonaris code.

## **Professional Workflows**

Sonaris is designed for practical quality-control scenarios beyond consumer playlist cleanup.

- **Catalog Ingest QA:** Validate incoming libraries for lossy transcodes hidden in lossless containers.
- **Master Delivery Validation:** Verify spectral bandwidth, clipping risk, and dynamic behavior before release.
- **Archive Audits:** Profile large historical collections with consistent, repeatable grading criteria.
- **Distribution Checks:** Compare codec/bitrate claims against measured spectral and loudness characteristics.
- **Forensic Screening:** Quickly identify suspect files for deeper review in DAWs and restoration suites.

Sonaris is a QA and verification tool. It complements DAWs/editors (such as WaveShaper and MixForge) rather than replacing production/mixing/mastering workflows.

## **Installation**

1. Download the latest release from the [Releases](https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/releases) page.
2. Run the installer and follow the setup wizard.
3. Launch Sonaris from the Start Menu or Desktop shortcut.
4. On first launch, FFmpeg tools are downloaded automatically. Wait for the status bar to show "Tools ready" before starting a scan.

## **Getting Started Guide**

### **Step 1: Select Files or Folders**

When you open Sonaris, the Analyze Files page is displayed with a drop zone in the center. You have three options to start an analysis:

- **Drag & Drop:** Drag a folder or individual audio files directly onto the drop zone
- **Browse Folder:** Click the "Browse Folder" button to select an entire directory for recursive scanning
- **Browse Files:** Click the "Browse Files" button to select individual audio files for analysis

### **Step 2: Review Scan Results**

After starting a scan, Sonaris automatically switches to the Results page where you can monitor progress in real time:

- **Grade Distribution:** A horizontal bar visualization shows the distribution of S, A, B, C, D, and F grades as files are analyzed
- **Folder Results:** Each scanned folder appears as a row with its overall grade, file count, codec, and key metrics
- **Track Details:** Click on any folder to view detailed per-track information including cutoff frequency, bitrate, loudness, dynamic range, stereo correlation, and mastering quality

### **Step 3: Export or Browse History**

Once the scan is complete, use the header buttons to export or save your results:

- **Copy Results:** Copies a formatted summary to the clipboard
- **Export:** One export dialog supports `TXT`, `CSV`, and `JSON` output formats

All past scans are stored in the Scan History page and can be reviewed at any time.

## **Quality Grading System**

Sonaris assigns quality grades based on the measured spectral content of each audio file. The grade reflects the highest frequency at which meaningful audio content is present, determined through FFT-based spectral analysis.

### **Absolute Grades**

| Grade | Cutoff Threshold | Description |
|-------|-----------------|-------------|
| **S** | >= 20 kHz | Full CD bandwidth, no perceptible quality loss |
| **A** | >= 18 kHz | Near-transparent quality (equivalent to high-bitrate lossy encoding) |
| **B** | >= 16.5 kHz | Good quality (equivalent to mid-bitrate lossy encoding) |
| **C** | >= 15 kHz | Acceptable quality for standard streaming |
| **D** | >= 12 kHz | Audible degradation with noticeable high-frequency loss |
| **F** | < 12 kHz | Severe quality loss, speech-grade or corrupted audio |

### **Source-Profile Relative Grades**

When platform detection is enabled, Sonaris adjusts grading thresholds based on the maximum achievable frequency for a detected source profile. This optional mode is useful for context-specific catalogs (for example, legacy console archives), while absolute grading remains available for general music, mastering, and library QA workflows.

## **Mastering Quality Assessment**

In addition to frequency-based grading, Sonaris evaluates the mastering characteristics of each track using loudness and dynamics metrics:

| Rating | Description |
|--------|-------------|
| **Excellent** | Well-mastered with good dynamics (DR >= 12), proper headroom, and ideal loudness range |
| **Good** | Reasonable dynamics (DR >= 9), minor headroom issues |
| **Average** | Moderate compression (DR 6-9), typical modern commercial mastering |
| **Poor** | Heavy compression with loudness war characteristics (DR < 6) |
| **Clipped** | True peak >= 0 dBTP or clipped samples detected |

Mastering quality is assessed independently from the frequency grade. A track can have an S-grade frequency response but poor mastering quality if it suffers from excessive compression or clipping.

## **Analysis Features**

### **Spectrum Analysis**

Sonaris uses FFT-based frequency analysis with cascaded highpass filter probing to measure the true spectral content cutoff of each track. The analysis process filters the audio through progressively higher frequency bands to determine the point at which meaningful content ends. With multi-window analysis enabled, both the beginning and midpoint of each track are analyzed, and the results are averaged for improved accuracy.

### **Stereo Correlation**

When enabled, Sonaris measures the correlation between left and right audio channels:

- **1.0** - Perfectly correlated (mono content)
- **0.5 to 1.0** - Normal stereo content
- **0.0** - Completely decorrelated
- **-1.0** - Phase-inverted (indicates potential recording or encoding issues)

Median stereo correlation is reported at the folder level to identify libraries with unusual stereo characteristics.

### **Clipping Detection**

Sonaris detects digital clipping by counting samples that reach the maximum digital level (0 dBFS) and measuring inter-sample true peak levels. Files with true peak >= 0 dBTP or flat-factor values indicating consecutive identical samples at the digital ceiling are flagged as clipped.

### **Upsampling Detection**

Sonaris can identify files where lossy audio has been re-encoded into a lossless container (e.g., MP3 converted to FLAC). When the measured spectral cutoff is significantly below what the codec and bitrate should deliver, the file is flagged as likely upsampled or transcoded. This helps identify misleading "lossless" files that don't actually contain high-fidelity audio.

### **Track Classification**

Short audio clips under 15 seconds and files with names matching common sound effect patterns (jingle, SFX, fanfare, etc.) are automatically classified as non-music tracks. These are excluded from folder-level grade calculations to prevent short effects from skewing the overall quality assessment. Non-music tracks can optionally be included in exports via the Settings page.

## **Source Profile Detection (Optional)**

Sonaris can detect source profiles from folder and file naming patterns. When a profile is detected, grading context can be adjusted to reflect the practical quality ceiling for that source. This mode is optional and complements, not replaces, standard absolute grading.

**Supported Source Profiles (examples):**

| Category | Examples |
|----------|-----------|
| **Professional / Studio** | CD, DVD Audio, Blu-ray Audio, Studio 44.1/48/96/192 kHz, Broadcast, Streaming, Film/Cinema, Podcast/Voice |
| **Analog / Broadcast** | Vinyl (LP), Cassette, FM Radio, AM Radio |
| **Legacy / Archival (Optional)** | NES/Famicom, SNES/SFC, Genesis/Mega Drive, N64, PS1/PS2/PSX, Saturn, Dreamcast, GameCube, Wii/Wii U, Switch, Xbox families |
| **Legacy Computers / Arcade (Optional)** | Commodore 64/SID, MSX, PC-88, PC-98, X68000, FM Towns, Atari ST, CPS families, Neo Geo, Naomi, MAME |
| **Handheld (Optional)** | Game Boy families, GBA, Nintendo DS/3DS, PSP, PS Vita |

Source profile detection is optional and disabled by default. Enable it only when you need source-aware grading context for specific catalogs.

## **Export Options**

### **CSV Export**

Exports one row per folder with columns for folder name, grade, file count, codec, sample rate, bitrate, cutoff frequency, LUFS, true peak, dynamic range, stereo correlation, clip count, platform, and upsampling flags. Suitable for spreadsheet analysis and data processing.

### **JSON Export**

Exports the complete per-track analysis dataset as structured JSON. Includes all measured metrics for every analyzed file, making it suitable for custom processing or integration with other tools.

### **Text Report**

Generates a formatted plain-text report with headers, per-folder breakdowns, and summary statistics. Designed for human-readable review or archival purposes.

### **Copy to Clipboard**

Copies a formatted text summary of the current results to the system clipboard for quick sharing or pasting into documents.

## **Scan History**

All completed scans are stored in the Scan History page. Each entry shows the scan date, folder name, number of files analyzed, scan duration, and a grade summary label (Excellent, Very Good, Good, Mediocre, Poor, Very Poor). Use the **View** button to load past results into the Scan Results page, or **Rescan** to re-analyze the same folder. Multiple history entries can be viewed simultaneously by using the View button on different entries.

Clear the scan history via the "Clear History" button in the Application Settings page header.

## **Settings**

### **Analysis Settings**

| Setting | Description | Options |
|---------|-------------|---------|
| **Samples per Folder** | Number of tracks to sample from each folder | 5, 10, 15, 20, All |
| **Analysis Duration** | Duration in seconds to analyze per file | 10, 20, 30, 60 |
| **Parallel Workers** | Number of concurrent analysis threads | 1, 2, 4, 8 |
| **Per-File Timeout** | Maximum seconds allowed per file analysis | 30, 60, 120, 300 |
| **Default Source Profile** | Auto-applied source profile override for every new scan | None (auto-detect), or specific profile |
| **Max Scan Depth** | Limit recursive subdirectory depth during folder scans | Unlimited, 1, 2, 3, 5 |
| **Min File Duration** | Skip files shorter than this duration | No minimum, 5s, 10s, 30s |
| **Multi-Window Analysis** | Analyze both start and midpoint of each track | On / Off |
| **Source Profile Detection** | Detect source profiles from folder names | On / Off |

### **Advanced Analysis**

| Setting | Description | Default |
|---------|-------------|---------|
| **Stereo Analysis** | Measure left/right channel correlation | Enabled |
| **Clipping Detection** | Detect digital clipping and flat-factor | Enabled |
| **Mastering Quality** | Assess mastering via LUFS, DR, and true peak | Enabled |

### **Export Settings**

| Setting | Description |
|---------|-------------|
| **Default Export Folder** | Directory where exported files are saved |
| **Include Non-Music** | Include sound effects and jingles in exported reports |

## **Cloud Settings Sync**

Sonaris supports cloud synchronization of settings through [Arctisoft Hub](https://github.com/BerndHagen/Arctisoft-Studio-Hub). Sign in once through the Hub and your analysis configuration is automatically synced across all devices.

Synced settings include all analysis parameters, advanced analysis toggles, and export preferences. Scan history is also stored in the cloud for cross-device access.

## **Keyboard Shortcuts**

| Shortcut | Description |
|----------|-------------|
| `Ctrl+1` | Navigate to Analyze Files page |
| `Ctrl+2` | Navigate to Results page |
| `Ctrl+3` | Navigate to Scan History |
| `Ctrl+4` | Navigate to Settings |
| `F5` | Navigate to Analyze Files page |
| `Ctrl+O` | Navigate to Analyze Files page |
| `Esc` | Close detail panel |

## **Copyright**

This software is freeware. You may use it for personal and commercial purposes.

Redistribution is permitted only in its original form with credit to the author.

Modification, decompiling, or reverse-engineering is prohibited without prior written consent.

Sonaris is provided "as is" without warranty. The author is not liable for any damages resulting from use.

See the [LICENSE](https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/blob/main/LICENSE) file for full terms.

## **Screenshots**

If you'd like a preview of Sonaris before downloading, the screenshots below show the application's features. Note that future updates may introduce additional functionality.

<table>
  <tr>
    <th>Sonaris - Analyze Files</th>
    <th>Sonaris - Live Scan Progress</th>
  </tr>
  <tr>
    <td><a href="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-start.png" target="_blank" rel="noopener noreferrer"><img src="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-start.png" alt="Sonaris Analyze Files" width="450"></a></td>
    <td><a href="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-scan.png" target="_blank" rel="noopener noreferrer"><img src="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-scan.png" alt="Sonaris Live Scan Progress" width="450"></a></td>
  </tr>
  <tr>
    <th>Sonaris - Scan Results</th>
    <th>Sonaris - Multi-Folder Results</th>
  </tr>
  <tr>
    <td><a href="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-results.png" target="_blank" rel="noopener noreferrer"><img src="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-results.png" alt="Sonaris Scan Results" width="450"></a></td>
    <td><a href="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-foldersresult.png" target="_blank" rel="noopener noreferrer"><img src="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-foldersresult.png" alt="Sonaris Multi-Folder Results" width="450"></a></td>
  </tr>
  <tr>
    <th>Sonaris - Scan History</th>
    <th>Sonaris - Application Settings</th>
  </tr>
  <tr>
    <td><a href="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-history.png" target="_blank" rel="noopener noreferrer"><img src="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-history.png" alt="Sonaris Scan History" width="450"></a></td>
    <td><a href="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-settings.png" target="_blank" rel="noopener noreferrer"><img src="https://github.com/BerndHagen/Sonaris-Audio-Quality-Analyzer/raw/main/images/screenshot-settings.png" alt="Sonaris Application Settings" width="450"></a></td>
  </tr>
</table>
