# Asteroseismic Analysis of 16 Cygni A Using Kepler Photometric Light Curves

A reproducible Python notebook for exploring stellar oscillations in **16 Cygni A** using photometric observations from NASA's Kepler mission.

- **Target:** 16 Cygni A
- **Kepler Input Catalog (KIC):** 12069424
- **Domain:** Astronomy, astrophysics, and scientific computing
- **Main file:** `16_Cygni_A_CODEFILE.ipynb`

## Project overview

Asteroseismology studies a star's internal properties by analysing its oscillations. These oscillations can produce very small variations in a star's observed brightness. This project uses a Kepler light curve and frequency-domain analysis to explore whether candidate oscillation features can be identified in 16 Cygni A.

The notebook is an exploratory computational workflow, not a claim of a new astrophysical discovery. Candidate measurements must be checked against the data quality, frequency resolution, noise, processing choices, and published research.

## Research question

Can small periodic variations in the observed brightness of 16 Cygni A be analysed to identify stellar oscillation frequencies, and how closely do candidate frequency patterns agree with published asteroseismic measurements?

## Published comparison values

The accompanying project report cites the following reference values from White et al. (2013):

| Parameter | Published reference |
|---|---:|
| Frequency of maximum oscillation power, `νmax` | `2201 ± 20 μHz` |
| Large frequency separation, `Δν` | `103.5 ± 0.1 μHz` |

These are reference values from the literature, **not guaranteed outputs** of the notebook. The notebook's estimates are exploratory and should not be treated as validated measurements without further analysis.

## Workflow in the notebook

1. Import the Python libraries and define the target and reference values.
2. Search the Kepler archive for light-curve products associated with KIC 12069424.
3. Download available products and combine them into a light curve.
4. Inspect the observations and normalise the flux.
5. Remove outliers using a 5-sigma filter.
6. Calculate a Lomb–Scargle periodogram over a selected frequency range.
7. Smooth the power spectrum to obtain an exploratory estimate of `νmax`.
8. Investigate `Δν` using an autocorrelation-based approach around the oscillation-power envelope.
9. Compare candidate values with published reference values.
10. Save the processed light curve and parameter comparison as CSV files.

## Requirements

Use Python 3. A recent Python environment is recommended.

The notebook uses these libraries:

- `lightkurve` — searching for and working with Kepler light-curve data
- `numpy` — numerical calculations
- `pandas` — tabular data and CSV output
- `matplotlib` — plots
- `scipy` — smoothing and signal-processing utilities
- `astropy` — astronomical units and time-series support
- `jupyter` — running the notebook

Install the dependencies from a terminal or command prompt:

```bash
python -m pip install jupyter lightkurve numpy pandas matplotlib scipy astropy
```

If `python` does not point to your Python 3 installation on your system, try `py -m pip` on Windows or `python3 -m pip` on macOS/Linux.

## How to run

1. Download or clone this repository to your computer.
2. Open a terminal/command prompt in the project folder.
3. Install the dependencies using the command above.
4. Start Jupyter:

   ```bash
   python -m jupyter notebook
   ```

5. Open `16_Cygni_A_CODEFILE.ipynb` in the browser tab that opens.
6. Run the cells from top to bottom. The archive search and download steps require an internet connection.
7. Review the plots, printed information, and comparison table. Check any warnings or errors rather than assuming that every archive product is suitable.

## Files produced by the notebook

When the final notebook cell runs successfully, it saves these files in the current working directory:

- `16_Cygni_A_processed_light_curve.csv` — processed observation times and normalised flux
- `16_Cygni_A_parameter_comparison.csv` — candidate `νmax` and `Δν` values compared with the cited reference values

The notebook also displays plots of the light curve, processed data, power spectrum, and the exploratory frequency-spacing analysis.

## Important interpretation notes

- The notebook searches for Kepler light-curve products without restricting the search to short cadence. The available cadence and observing duration should therefore be inspected before interpreting the results.
- Removing outliers and smoothing a power spectrum can affect the apparent signal. The chosen settings should be documented and tested for sensitivity.
- The tallest spectral peak alone does not prove the presence of a stellar oscillation mode.
- The large frequency separation is associated with the spacing of appropriate oscillation modes; an exploratory autocorrelation result is not automatically a reliable `Δν` measurement.
- Data gaps, instrumental noise, finite observation duration, and the frequency resolution can limit the analysis.
- Only conclusions supported by the actual downloaded data should be reported.

## References

1. White, T. R., et al. (2013). “Interferometric radii of bright Kepler stars with the CHARA Array: θ Cygni and 16 Cygni A and B.” *Monthly Notices of the Royal Astronomical Society*, 433(2), 1262–1270. https://doi.org/10.1093/mnras/stt802
2. Lightkurve Collaboration. *Lightkurve Documentation: Searching for and Downloading Kepler and TESS Data.* https://lightkurve.github.io/lightkurve/tutorials/1-getting-started/searching-for-data-products.html
3. NASA Mikulski Archive for Space Telescopes (MAST). https://mast.stsci.edu/
