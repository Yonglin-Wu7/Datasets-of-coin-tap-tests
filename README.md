# Datasets-of-coin-tap-tests
We do coin-tap tests for three types of bi-layered structures (aluminum bi-layer, polymethyl methacrylate bi-layer, and glass-fiber reinforced polymer bi-layer) to obtain acoustic signals. Then, we constructed this dataset and saved it in pkl file format.
The dataset is organized in the form of nested dictionaries, with specific levels as follows:
1. Top level key: Material type ('Al ','Acrylic', 'GFRP')
2. Each sample (dictionary structure):
{
    'xy': (x, y),          # Two dimensional coordinates representing the position of the tapping point.
    'data': np.ndarray,     # One dimensional array, storing time series data of acoustic signals.
    'label': int            # labels from 0 to 6 referring to: Normal, large-area cavity , bubble-like cavity, large-area top disbond, bubble-like top disbond, large-area bottom disbond, and bubble-like bottom disbond.
}
3.
