# SmartFit: Personalized 3D Human Body Modeling  

![Creating by Deform-Based Global Mapping](https://raw.githubusercontent.com/1900zyh/3D-Human-Body-Shape/master/docs/dg-h.png)

SmartFit: Personalized 3D Human Body Modeling  
  


## Introduction  

The rise of e-commerce has revolutionized how consumers shop, yet the inability to physically try on clothes poses challenges. This project presents **SmartFit**, a system designed for personalized 3D human body reshaping. By combining advanced anthropometric modeling, machine learning, and 3D rendering, SmartFit bridges the gap between online and in-store shopping experiences.  

The system leverages cutting-edge technologies like **MICE** for missing data imputation and feature-selection-based mapping methods to generate realistic 3D body models from limited parameters (e.g., height, weight). This personalized solution reduces uncertainty in selecting sizes and styles, enhancing customer satisfaction and minimizing returns.  



## Approach  

The SmartFit system operates in two stages: **offline training** and **online execution**, with three core components: the Imputer, Selector, and Mapper.  

1. **Offline Stage**:  
   - A dataset of 3D body meshes (a) and anthropometric parameters (b) trains relevance masks (c) using feature-selection-based mapping.  
   - Mapping matrices (d) are generated via linear regression, enabling conversion from parameters to body meshes.  

2. **Online Stage**:  
   - User-provided inputs (e) with missing data (‘?’) are completed using **MICE** for imputation (f).  
   - The completed parameter set (f) is passed to the Mapper, which uses pre-trained masks (c) and matrices (d) to generate the final 3D body mesh (g).  

![Framework](https://raw.githubusercontent.com/1900zyh/3D-Human-Body-Shape/master/docs/framework.PNG)



## Experiments  

The SmartFit system was validated against benchmark datasets, showcasing its accuracy across diverse body types. The results (see table below) emphasize the effectiveness of the mapping methods in delivering precise reshaping outcomes.  

<div align="center">
	<img src="https://raw.githubusercontent.com/1900zyh/3D-Human-Body-Shape/master/docs/table2.PNG" alt="Editor" width="500">
</div>



## Quick Start  

### Environment  

1. Compatible with Windows/OSX/Linux, Python 3.5.  
2. Install dependencies via:  
pip install -r requirements.txt



### Preparation  

1. Download training data from [SPRING](https://graphics.soe.ucsc.edu/data/BodyModels/index.html).  
2. Place datasets in the `3D-human-Body-Shape/data` directory.  
3. Clone the repository:  
git clone https://github.com/1900zyh/3D-Human-Body-Shape.git cd 3D-Human-Body-Shape/



### Training  

Run the following to train with your datasets:  
cd src/ python train.py


### Testing  

Test the system using the [released model](https://github.com/1900zyh/3D-Human-Body-Shape/tree/master/release_model):  
cd src/ python demo.py


## Demo  

1. **Adjust size**: Modify anthropometric parameters for simulation.  
   ![Demo Step 1](https://raw.githubusercontent.com/1900zyh/3D-Human-Body-Shape/master/docs/fig1.png)  

2. **Save**: Use `Ctrl + S` to save the 3D model (`.obj` file).  

3. **Switch Mapping Methods**: Select between global or local mapping strategies.  
   ![Demo Step 3](https://raw.githubusercontent.com/1900zyh/3D-Human-Body-Shape/master/docs/fig2.png)  

4. **Predict**: Input parameter values for prediction; defaults can be estimated.  
   ![Demo Step 4](https://raw.githubusercontent.com/1900zyh/3D-Human-Body-Shape/master/docs/fig3.png)  



## Different Mapping Methods  

1. **Global Mapping**  
2. **Local Mapping with Mask** ([Reference](https://dl.acm.org/citation.cfm?id=2758217))  
3. **Local Mapping with RFEMAT** ([Reference](https://link.springer.com/chapter/10.1007/978-981-10-))