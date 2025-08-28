# EV Motor–Inverter FDD (Simulation-Only) — Starter Pack
##
 This kit simulates a 3‑phase PMSM + simple sinusoidal PWM inverter, injects
 common faults, generates a labeled dataset, extracts features (time/freq), and
 trains baseline ML models (SVM / RandomForest).<br>A light “realtime” emulation
 loop is included.
##
## Subsystem & Faults (implemented):
• Inter‑turn short (one phase: effective L↓, R↑)<br>
• Phase open (one phase effectively disconnected)<br>
• Inverter switch short (phase clamped to ±Vdc/2)<br>
• Bearing fault (load torque ripple → current sidebands)<br>
• Eccentricity (back‑EMF amplitude modulation)
##
## Key signals: 
phase currents/voltages (ia, ib, ic, va, vb, vc), speed (omega),<br>
electrical angle (theta), DC link voltage.
##
## Quickstart
1) Install deps:    pip install -r requirements.txt<br>
2) Generate data:   python data_gen.py --out data/raw --n_scen 60 --seed 7<br>
3) Features:        python features.py --in data/raw --out data/features<br>
4) Train:           python models.py --features data/features<br>
5) Realtime demo:   python realtime_demo.py
##
### Notes

• The PMSM/inverter is deliberately simplified for speed + clarity.<br>
• Use the provided config ranges to create domain shift splits (unseen speeds).<br>
• Extend with STFT spectrogram → 2D‑CNN if desired.<br>
