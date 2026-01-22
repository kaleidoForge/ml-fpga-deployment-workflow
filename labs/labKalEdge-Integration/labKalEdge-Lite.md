![Workflow Overview](../../img/general/header_workflow.png)


# End-to-End ML to FPGA Deployment with KalEdge-Lite


## Objective

In this laboratory session, you will learn how to:

- Load and preprocess a dataset in **KalEdge-Lite**
- Configure and train different neural network architectures
- Compare model variants (Baseline, Student, QKeras)
- Generate an optimized FPGA implementation using **hls4ml**
- Export an HLS project ready for hardware synthesis

The workflow follows a complete **end-to-end pipeline**, from data ingestion to FPGA deployment.

---

## Pre-requisites

Before starting, make sure you have:

- Access to **KalEdge-Lite**
- A valid HyperFPGA instance
- Basic understanding of:
  - Neural networks
  - Model training
  - FPGA-based acceleration


---

### 1. Launch the Application

Open **KalEdge-Lite** using the following link:

https://kaledge-lite-64594466260.europe-west1.run.app

---

### 2. Load the Dataset

1. Open the **Dataset** panel.
2. From the dropdown menu, select **CSV (path)**.
3. Enter the following path:

    `/app/assets/gamma_neutron.csv'`


This dataset corresponds to the **gamma/neutron discrimination system**.

4. Leave the **Input** parameter set to **Auto**.

Once loaded, you should see a window similar to the one shown below.

![alt text](../../img/kalEdgeLite/dataset.png)

---

### 3. Define the Model Architecture

Go to the **Architecture** tab and select one of the predefined models.

For each model:

1. Click **Save**
2. Then click **Load into Pipeline**

Available options:

- **Baseline model**
- **Student model**
- **QKeras model**

---

### 4. Configure Training

In the **Training** window:

- Configure the training parameters if desired.
- You can train each model independently.
- For this tutorial, **leave all parameters as default**.

---

### 5. Configure the Pipeline

1. Go to the **Pipeline** tab.
2. In **Score Priorities**, select: **FPGA**.


---

### 6. Pipeline Builder

In the **Pipeline Builder** section:

- Leave all options at their default values.

---

### 7. Run the Pipeline

Click **Run Pipeline** and wait until the process completes.

---

### 8. Results

Once finished:

- A message **“Report generated”** will appear.
- Navigate to the **Reports & Export** tab. In this section, you can inspect the generated report. 

---

### 9. HLS Integration

Click on the **HLS4ML Integration** tab.

#### HLS / FPGA Settings

Configure the following:

1. **Target board**
- `HyperFPGA 4eg21`
- `HyperFPGA 3be11`

    >Note: Must match the FPGA instance assigned in HyperFPGA.

2. **Clock period**: 10ns

3. **Precision**: ap_fixed<16,6>

4.  **Reuse factor**: 8

5. **I/O type**: io_parallel

![alt text](../../img/kalEdgeLite/hls4ml-Export.png)

---

### 11. Generate HLS Project

Click:

➡ **Convert to HLS**

Wait until the conversion process finishes.

---

### 12. Visualization

Click **Show Confusion Matrix** to visualize the classification performance.

---

### 13. Download

Finally:

- Download the **HLS project with ComBlock support**
- The project is now ready for FPGA synthesis and deployment


## Automate IP core generation and hardware creation 

In this step, we are going to use some sripts to generate the IP core and the .xsa file (this is going to be upload to the HyperFPGA)