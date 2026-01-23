# Smart‑City Delivery Optimization (AI & Pathfinding)

This project predicts traversal costs for urban road segments with machine learning and uses those predictions to select optimal delivery routes. It also includes a reinforcement‑learning (Q‑learning) agent that learns to navigate a grid environment and a shortest‑path implementation (Dijkstra) to compute routes using predicted traversal costs.

Key highlights
- Predicts traversal cost (a continuous label) from features such as elevation, traffic speed, pollution, population density, road quality, proximity to main roads, weather index and categorical features (terrain type, zone classification, time of day).
- Compares classical regression (including polynomial regression) with neural networks (Keras/TensorFlow) for traversal‑cost prediction.
- Uses predicted traversal costs to build weighted graphs and compute optimal routes with Dijkstra’s algorithm.
- Implements a Q‑learning agent for a 5×5 grid environment that reliably reaches its goal (demonstrates RL baseline / agent behavior).

Repository structure
- AI coursework.ipynb — Main Jupyter notebook containing data exploration, preprocessing, modeling, training logs, evaluation and pathfinding/Q‑learning experiments.
- README.md — (this file) project summary and usage.
- (If you have additional files such as a written report PDF, put it here and tell me the path — I couldn’t find one in the repo.)

Dataset (as used in the notebook)
- Observed columns (examples): elevation, avg_traffic_speed, pollution_level, population_density, road_quality_index, proximity_main_roads, weather_condition_index, type_of_terrain, zone_classification, time_of_day, traversal_cost
- The notebook shows experiments on a dataset of 20,000 rows (as printed by dataset.info()).

Methods implemented
- Data exploration and preprocessing
  - Identification of numerical and non‑numerical features
  - One‑hot encoding for categorical features (type_of_terrain, zone_classification, time_of_day)
  - Train/test split
- Regression models
  - Polynomial regression (baseline comparison)
  - Feedforward neural network(s) implemented in Keras (models trained for multiple epochs; training logs and validation MAE printed in the notebook)
  - Evaluation using MAE and comparison between actual and predicted traversal costs
- Pathfinding
  - Construct a graph where edges are weighted by predicted traversal cost and compute shortest paths using Dijkstra’s algorithm.
- Reinforcement learning
  - Q‑learning agent trained and evaluated in a 5×5 grid environment; agent reliably reaches the goal in experiments reported in the notebook.

Example results (from notebook)
- Neural-network training logs show validation MAE values in the notebook outputs (example runs show MAE values on the order of ~60–80 depending on model and hyperparameters).
- Q‑learning agent: consistently reached its goal in a 5×5 environment (demonstrates basic agent performance).

Usage — run locally
1. Clone the repository
   git clone https://github.com/<your-username>/A.I-modle-course-work-.git
2. Create and activate a Python environment (recommended)
   python -m venv venv
   source venv/bin/activate  # macOS/Linux
   venv\Scripts\activate     # Windows
3. Install dependencies (example)
   pip install jupyterlab pandas numpy scikit-learn matplotlib seaborn tensorflow networkx
   - If you use a CUDA-enabled GPU and TensorFlow GPU build, install the appropriate tensorflow package.
4. Launch the notebook
   jupyter lab
   - Open `AI coursework.ipynb` and run the cells in order.

Dependencies (from notebook needs)
- Python 3.8+ (recommended)
- pandas, numpy
- scikit-learn
- matplotlib, seaborn
- tensorflow (or tensorflow-cpu)
- networkx (or another graph library used for Dijkstra)
- jupyter / jupyterlab

Reproducing experiments
- The notebook is organized to:
  1. Load dataset and print dataset.info()
  2. Preprocess features (one‑hot encoding for categorical features)
  3. Train regression models (polynomial regression and Keras models)
  4. Evaluate on test set (MAE and actual vs predicted tables are printed)
  5. Build graph and run Dijkstra on predicted edge weights to find optimal routes
  6. Run and evaluate Q‑learning agent in a 5×5 grid environment
- To reproduce results, run all cells in order. If random seeds are required for exact reproducibility, set seeds for numpy, tensorflow and any other libraries at the top of the notebook.

Suggested next steps and improvements
- Add a requirements.txt or environment.yml with pinned package versions for reproducibility.
- Move long training runs and heavy computations into scripts so the notebook focuses on explanation and experiment summaries; save model weights and artifacts to disk.
- Add unit tests for core components (data preprocessing, model evaluation scripts, graph construction, pathfinding).
- Hyperparameter search and cross‑validation for more robust model selection.
- Evaluate prediction errors by region/terrain or time_of_day to discover systematic biases.
- If available, include the written project report (PDF) in the repo; I can extract the report’s executive summary and incorporate it into this README.

If you want, I can:
- Update this README based on the written PDF if you upload it or tell me where it is in the repo.
- Create a requirements.txt from the notebook imports and package versions.
- Split the notebook into: a short explanatory notebook + scripts for training and evaluation.

Contact
- Repo owner / author: @Musyoka7
- If you want me to include a "How to cite" section or licensing, tell me which license to add (e.g., MIT, Apache‑2.0).