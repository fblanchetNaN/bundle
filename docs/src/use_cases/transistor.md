# DC Characterization of a transistor

## Problem description

Transistor are made of three terminals: source, drain and gate, a possible characterization is to apply DC voltages
between source-drain and gate-drain and measure both flowing currents.

In python + numpy, it may look like
```python
for drain_voltage in np.linspace(0,10,101):
    # VISA command to apply drain_voltage
    for gate_voltage in np.linspace(0,10,101):
        # VISA command to apply gate_voltage
        # VISA command to measure drain_current
        # VISA command to measure gate_current
        # store results on disk
```
However, as number of parameters can increase, those inner loops structure become complex to write and even more
to maintain.

## Needs
Syntactic sugar / DSL to ease:
- Expressing a multiple inner loops structure (with setting parameters)
- Storing the results

Moreover, this structure can fail at any time (e.g. if an instrument is disconnected), but the dataset result have to
remain valid.
