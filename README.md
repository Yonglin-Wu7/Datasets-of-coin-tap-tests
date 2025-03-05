# Datasets of coin-tap tests
We do coin-tap tests for three types of bi-layered structures (aluminum bi-layer, polymethyl methacrylate bi-layer, and glass-fiber reinforced polymer bi-layer) to obtain acoustic signals. Then, we constructed this dataset and saved it in pkl file format.
The dataset is organized in the form of nested dictionaries, with specific levels as follows:
1. Top level key: Material type ('Al ','Acrylic', 'GFRP')
2. Subkeys: Initial three subsets ('1 ','2','3 ')
3. Each sample (dictionary structure):
{
    'xy': (x, y),          # Two dimensional coordinates representing the position of the tapping point.
    'data': np.ndarray,     # One dimensional array, storing time series data of acoustic signals.
    'label': int            # labels from 0 to 6 referring to: Normal, large-area cavity , bubble-like cavity, large-area top disbond, bubble-like top disbond, large-area bottom disbond, and bubble-like bottom disbond.
}

# Example data access: Obtain the first sample of sub key '1'
import pickle
with open("Coin_tap_data_Al.pkl", "rb") as file:
    data = pickle.load(file)
subset_1_samples = data['Al']['1']
sample_1 = subset_1_samples[0] 

# Experimental details
Preparation of test samples and defects: We use bi-layer samples bonded by soft adhesive (the thickness of the plates is 1 mm) in experiments. The defects are fabricated in the following ways. For cavities, we remove the inner soft adhesive. For disbonds, we insert separation films to make the plates and the adhesive separated (the separation film is thin enough to be negligible). Top and bottom disbonds are prepared by flipping the bonded plates. When the separation film is on top of the adhesive, it is top disbonding. When the separation film is on the bottom of the adhesive, it becomes bottom disbonding. The shapes of large-area defects are rectangles and rounded rectangles of sizes 10 mm and 20 mm. The bubble-like defects are circulars with diameters of 3 mm and 4 mm. All the defects are at the depth range of 1 mm to 2 mm. These defects are produced by using a laser cutting machine before the plates bounded together.
Coin-tap test: We design an automated test rig to acquire acoustic signals. The test rig consists of an electromagnet for tapping (travel range: 0~10mm, force range: 2N~20N), a rubber buffer (30mm thick), a slider (positioning accuracy: 0.05mm), a microphone, and three specimen fixtures. The programmed testing process is controlled automatically. The tapping force is controlled by setting a constant short charging time of the electromagnet. The test rig is programmed to scan a 200 mm × 200 mm test area on each side of the specimen in a stride of 2 mm. We use the sampling rate of 48 kHz. The collected acoustic signals are first processed into samples of the same length (2048). Then, the samples are labeled on the prefabricated defect map according to the tapping position.
For more specific experimental details, please refer to the academic paper 'Data-driven deep representation of acoustic signals amplifies the accuracy of coin-tap test for non-destructive detection of defects'.
