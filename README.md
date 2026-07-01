# Route Continuity Gap Detector

A geospatial quality assurance tool that automatically finds gaps and errors in road networks. Upload a WKT geometry file and the app identifies endpoint gaps, isolated segments, and short dead-end fragments, then plots every issue on an interactive map.

Built for the IIT Mandi x Masai School x Axes Systems Hackathon.

**Live app:** [gapdetectorhackathon30-jhx7edzznqoz3mdrvfgkb2.streamlit.app](https://gapdetectorhackathon30-jhx7edzznqoz3mdrvfgkb2.streamlit.app/)

## What it does

- **WKT parsing** - reads standard Well-Known Text geometry files representing road segments as `LINESTRING` features
- **Endpoint gap detection** - finds line endpoints that are close but not connected, using Shapely spatial analysis
- **Isolation detection** - identifies segments with no connections to any other segment, using an unsupervised Isolation Forest model (scikit-learn)
- **Short segment detection** - flags fragments below a configurable length threshold
- **Interactive map** - all detected errors plotted on a Folium/Leaflet map with colour-coded markers by error type
- **Downloadable results** - export gap coordinates as CSV for downstream QA work

## Stack

| Layer | Technology |
|---|---|
| UI | Streamlit |
| Geometry | Shapely 2.x |
| ML | scikit-learn (Isolation Forest) |
| Data | pandas, numpy |
| Maps | Folium, streamlit-folium |
| Language | Python 3 |

## Running locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

Upload a `.wkt` file containing `LINESTRING` geometries, one per line. Demo files covering different error scenarios are in `demo_files/`.

## Hackathon context

This project addresses Problem Statement 2 from the IIT Mandi x Masai School x Axes Systems hackathon: build a tool that detects continuity errors in road network data supplied as WKT geometry. The original problem statement and supporting documentation are in `Problem Statement 2/`.
