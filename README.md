# 🧠 Mouse Position Prediction from Neural Signals

This project explores the use of deep learning models to predict 2D mouse position from neural time-series data. The neural data is preprocessed and passed into different model architectures including **Multi-Layer Perceptrons (MLPs)** and a **Transformer Encoder**.

## 📁 Dataset

- The dataset is sourced from a `.mat` file:  
  `delta_reach_20080724-111450-001_Processed.mat`
- It contains:
  - `neural_data_pro`: neural signal features
  - `mouse_position`: (X, Y) coordinates
  - `time_base`: time vector

The dataset is split into 90% training and 10% validation in a sequential manner to preserve temporal structure.

## 🧠 Models Tested

Three architectures were tested to regress the mouse's X/Y coordinates from neural features:

### 1. **3-Layer MLP with Dropout 0.3**
- Dropout applied after each GELU activation
- Hidden layer sizes: 256 → 128 → 64
- Output: 2 neurons for X and Y
- Epochs: 33
- Performance: R² score calculated on validation set

### 2. **3-Layer MLP with Dropout 0.2**
- Similar to above but with reduced dropout for improved generalization in low-variance regimes
- Epochs: 10

### 3. **Transformer Encoder**
- [Not included in this snippet, but implemented in separate script]
- Suitable for capturing temporal dependencies across signal windows

## 🔍 Preprocessing

- All neural inputs and output positions were **standardized using z-score normalization**
- Data was converted into PyTorch tensors and loaded using `DataLoader`

## 📈 Training Setup

- Loss Function: `MSELoss`
- Optimizer: `Adam` with learning rate `0.001`
- Batch Size: 64
- Training is deterministic using fixed seeds for reproducibility

## 📊 Evaluation

- Final model predictions are **inverse transformed** to original scale
- Metric: `R² Score` between actual and predicted positions
- Visualization:
  - X and Y position vs time
  - Actual vs Predicted 2D trajectory

## 🖼️ Sample Output

- **Predicted vs Actual X and Y Time Series**  
  Shows model tracking capability over time

- **2D Mouse Trajectory**  
  Overlay of predicted path on the true trajectory

## 🚀 Future Work

- Incorporating **temporal windowing** for sequence learning
- Tuning Transformer model for longer neural traces
- Cross-validation and ablation studies on dropout rates

## 🛠️ Tech Stack

- Python, PyTorch, NumPy, SciPy, Matplotlib
- Data Format: MATLAB `.mat` file

---

### 📬 Contact

For questions or collaboration, feel free to connect on [LinkedIn](https://www.linkedin.com/in/kanav99/) or open an issue in this repo.

