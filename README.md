# MobiAnon: Mobility Privacy Demonstrator

MobiAnon is a full-stack React, Express, and MySQL demonstrator for exploring explainable privacy protection on point-to-point mobility trip data. It compares original trip records with anonymized releases and reports privacy/utility metrics such as k-violations, l-diversity violations, suppression, spatial error, density similarity, hotspot overlap, and backend timing.

The project is designed as a research/demo tool, not a production anonymization framework. Its main goal is to make privacy-utility tradeoffs visible through maps, controls, metrics, upload workflows, sample data, benchmark scripts, and an interactive 3D privacy-utility landscape.


---

## Project Background & Research Contributions

### Master's Thesis — Original Development

**Haris Mustafa | University of Bamberg**

MobiAnon builds upon my Master's thesis research on explainable anonymization techniques for mobility data.

I developed the original interactive web demonstrator to investigate and visualize the privacy-utility trade-off in mobility datasets using spatial k-anonymity.

The original demonstrator included:

- Interactive visualization of original and anonymized mobility data.
- Spatial grid-based anonymization with configurable k-values and grid sizes.
- Side-by-side geographical comparisons of original and anonymized trip records.
- Interactive maps, trip visualization, and geographical heatmaps.
- Filtering of mobility data by date and rider membership type.
- Visual exploration of how anonymization parameters affect data utility.

As part of the thesis research, the demonstrator was evaluated in a user study involving **16 participants**, exploring how interactive visualizations help users understand data anonymization and its effects.

**Live Thesis Demonstrator:** https://harismustafa.info/

### Continued Development — MobiAnon

Following the completion of my Master's thesis, the original demonstrator became the foundation for further collaborative research and development.

The extended project, **MobiAnon**, integrates additional privacy-preserving techniques, data processing capabilities, interactive visualizations, and reproducible evaluation methods.

The extended application includes:

- Spatial and spatio-temporal k-anonymity.
- Optional l-diversity and differential privacy mechanisms.
- Temporal generalization for mobility records.
- Full-stack architecture using React, Node.js, Express, and MySQL.
- Interactive geographical maps and privacy-utility comparisons.
- Multi-k comparison and interactive 3D privacy-utility visualization.
- CSV dataset upload, validation, and resumable data import.
- Quantitative utility metrics and reproducible benchmarking.
- Evaluation using real-world Citi Bike and Hubway mobility datasets.

This extension was developed through research collaboration and builds directly upon the original thesis demonstrator.

### Research Publication & Conference — SKILL 2026

**Paper Title:**

*MobiAnon: An Interactive Demonstrator for Exploring the Privacy-Utility Trade-off in Mobility Data*

**Authors:**

1. Muhammad Tayyab Shafique
2. **Haris Mustafa**
3. Abeera Ayesha Riaz

**Conference:** SKILL 2026 — Studierendenkonferenz Informatik

**Location:** Dresden, Germany

**Event:** Informatik Festival 2026

**Research Contribution:**

The paper presents MobiAnon as an interactive demonstrator for exploring privacy-preserving techniques in mobility datasets. It discusses the system architecture, anonymization pipeline, visualizations, and quantitative evaluation of the privacy-utility trade-off.

The research was accepted for presentation at SKILL 2026, where the project and its findings were presented.

### Project Links

- **My GitHub Repository:** https://github.com/Harismustafa-atd/MobiAnon
- **Live Master's Thesis Demonstrator:** https://harismustafa.info/
- **Original Collaborative Repository:** https://github.com/MTayabShafique/MobiAnon

### Development & Research Attribution

The original Master's thesis demonstrator was developed by **Haris Mustafa** at the University of Bamberg.

MobiAnon is an extended collaborative research project building upon this initial work.

The research paper was co-authored by Muhammad Tayyab Shafique, Haris Mustafa, and Abeera Ayesha Riaz.

This repository is maintained as a fork of the collaborative MobiAnon repository, preserving its development history and attribution to the original contributors.

---


The project supports:

- Original vs anonymized map comparison.
- Spatial and spatio-temporal k-anonymity.
- Temporal privacy modes: spatial-only, day, period, and hour.
- Optional l-diversity for rider type, bike type, destination area, gender, and age band.
- Optional epsilon-DP-style Laplace noise on released centroids and counts.
- Multi-k comparison for selected k values.
- Upload of Citi Bike, Divvy, Hubway/Bluebikes-style, or similar mobility CSV files.
- Global latitude/longitude validation instead of NYC-only uploads.
- Resumable 5,000-row chunk upload with retry.
- Clear-all-user-data workflow with streamed delete progress.
- Downloadable minimal, Divvy, Citi Bike, and Hubway sample CSVs.
- Optional Hubway-style metadata: `tripduration`, `bike_id`, `gender`, `birth_year`, and derived `age_band`.
- Dynamic data-source bounds and date ranges for uploaded datasets.
- Light/dark UI themes for demos and screenshots.
- Interactive 3D privacy-utility landscape for k-anonymity, l-diversity, and epsilon-DP scenarios.
- Benchmark scripts and paper-ready report/figure generation.
- Suppression-only and fixed-grid baseline comparison against the merge-nearest anonymization method.

## Visual Overview

The submitted paper focuses on the architecture, anonymization pipeline, and benchmark results. The screenshots below show the application interface that reviewers can inspect when they open this repository.

### 1. Main Tool: Original vs Anonymized Trips

![Main Tool: Original vs Anonymized Trips](readme_assets/01-tool-overview.png)

This is the core MobiAnon interaction: raw mobility trips are shown next to the anonymized release so users can visually compare spatial patterns and utility loss.

### 2. Privacy Settings and Metrics

![Privacy Settings and Metrics](readme_assets/02-privacy-settings-and-metrics.png)

The controls expose grid size, k, temporal privacy, l-diversity, sensitive attributes, and epsilon-DP noise. The metric cards summarize privacy validity and utility loss in the same view.

### 3. Multi-k Comparison

![Multi-k Comparison](readme_assets/03-multi-k-comparison.png)

The comparison panel runs the same query for multiple k values, helping users see how stronger anonymity changes suppression, spatial error, density similarity, and hotspot overlap.

### 4. 3D Privacy-Utility Landscape

![3D Privacy-Utility Landscape](readme_assets/04-3d-privacy-utility-landscape.png)

The 3D landscape gives an interactive overview of privacy-utility tradeoffs across k-anonymity, l-diversity, and epsilon-DP scenarios.

### 5. Upload and Data Management: Resumable Import

![Upload and Data Management: Resumable Import](readme_assets/05-upload-and-data-management-during-upload.png)

The upload page supports user mobility CSV files, sample downloads, resumable chunk upload, and duplicate handling. This screenshot shows a Citi Bike sample being imported in chunks while the application keeps upload progress visible.

### 6. Upload and Data Management: Import Summary

![Upload and Data Management: Import Summary](readme_assets/06-upload-and-data-management-success.png)

After upload, the page reports rows read, records inserted, duplicate records, skipped rows, validation details, the active user-data count, and the detected date range that will drive the Tool page date picker.

### 7. Upload and Data Management: Clearing User Data

![Upload and Data Management: Clearing User Data](readme_assets/07-upload-and-data-management-during-delete.png)

Uploaded data is isolated from the preloaded demo data and can be cleared safely. The delete workflow streams batch progress so users can see how many records have been removed.

### 8. In-App Guide

![In-App Guide](readme_assets/08-in-app-guide.png)

The guide explains supported CSV formats, privacy models, metrics, and application workflow for users who are not privacy experts.

## Reproducibility

For setup, Laragon/MySQL instructions, database creation, data import, benchmark commands, report generation, and known limitations, see:

[REPRODUCIBILITY.md](./REPRODUCIBILITY.md)

That guide is the primary source of truth for reproducing the current version of the project.

## Quick Start

```bash
npm install
cd bicycle-be
npm install
cd ..
npm run dev
```

Frontend:

```text
http://localhost:5173
```

Backend:

```text
http://localhost:5000
```

## Important Paths

| Path | Purpose |
| --- | --- |
| `src/components/Map/MapCompare.jsx` | Main comparison UI |
| `src/components/Upload/CSVUpload.jsx` | CSV upload/data-source UI |
| `src/components/Viz3D/PrivacyLandscape.jsx` | Interactive 3D privacy-utility landscape |
| `src/pages/Guide.jsx` | In-app user guide |
| `bicycle-be/routes/bicycleRoute.js` | Trip/anonymization API routes |
| `bicycle-be/routes/uploadRoute.js` | CSV upload, sample download, source metadata, and delete API |
| `bicycle-be/services/anonymization.js` | k-anonymity, l-diversity, DP noise, metrics, and baseline methods |
| `bicycle-be/scripts/evaluateAnonymization.js` | Offline anonymization benchmark |
| `bicycle-be/scripts/generateBenchmarkReport.js` | Paper report/figure generation |
| `bicycle-be/scripts/benchmarkDbQueries.js` | Live database query benchmark |
| `bicycle-be/db/create-trips-table.sql` | Clean MySQL schema setup |
| `bicycle-be/db/performance-indexes.sql` | Live query performance indexes |
| `bicycle-be/paper-results/` | Generated paper-facing reports and figures |

## Verification

```bash
npm run build
cd bicycle-be
npm run benchmark:anonymization
npm run report:benchmark
npm run benchmark:db
npm run report:db
```

On managed Windows laptops, `npm run build` may need to be run in a normal terminal if a sandbox blocks the esbuild worker process.

## Scope Notes

- The app expects point-to-point trips with start/end timestamps and coordinates.
- Station-ID-only data, zone-only data, and full GPS trajectories need preprocessing before import.
- The epsilon-DP layer is a per-query demonstrator mechanism and does not include full privacy accounting across repeated API calls.
- Authentication components exist in the codebase, but the main Tool, Upload, and Guide routes are currently public.
