---
{"dg-publish":true,"permalink":"/dee-pmd/training-deep-md-on-silica-dft-simulations/","dgHomeLink":true,"dgPassFrontmatter":false}
---


We start by running a DFT simulation of some relevant silica system that explores some reasonable part of the configuration space that we are planning to target. For cracks in $\alpha$-quarts, it is probably wise with a combination of: 
| Simulation | Reason | Implementation |
|-----------------|-------------------| ---- |
| Relaxed alpha-quartz | Baseline | Relax alpha-quartz using DFT, then run MD with temperature ramp up to beta quartz | 
| Relaxed beta-quartz | Could occur during tensile fracture of alpha-quartz | Relax beta-quartz using DFT, then run MD with temperature ramp down to alpha quartz |
| Strained alpha and beta quartz | We will strain systems in production runs to make them crack | Perturbations using init_bulk in dpgen | 
| Amorphous silica | Targeting disordered states that may occur when the fracture progresses | Create amorphous silica using the vashishta potential. After a few generations of training, generate new amorphous structures using deepmd potential |
| Strained alpha/beta quartz with defects| Target particular configurations that occur in fractures | Relax structures with defects using DFT | 
| Silica surfaces | Cracks contain a surface | Relax slabs with vacuum above using DFT | 
| Nanoporous silica | To target disordered surfaces | Create nanoporpous silica by cooling an expanded silica melt. First with vashishta, then with deepmd potential | 

When we get `OUTCAR` files from VASP DFT simulations, we run the following command to turn them into DeePMD training data: 
```python 

```

When we have our training data, we execute the following command to train he model: 
```bash
dp train input.json
```


## Generating training data with dpgen
`dpgen` is a tool that facilitates the running of first principles (DFT, VASP) simulation, training of deepmd models and then exploration of configuration space using trained deepmd models. Data from these configuration space exlorations can the be run in DFT to procude a refined training dataset. 

Our approach will be: 
1) Generate a set of initial structures as given in the table above. 


## Configuration of VASP simulations 
There are several types of VASP simulations to be performed. They are mainly of three types: 
- Single configuration energy evaluation (in dpgen iterations)
- Structure optimization (For the initial crystal configurations)
- Molecular dynamics (For the initial exploration of configuration space)

We will use SCAN functionals for all simulations. 
For structure optimizations, we will use ...
For molecular dynamics we will run NpT with a Langevin thermostat. 