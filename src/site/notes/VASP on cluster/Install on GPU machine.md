---
{"dg-publish":true,"permalink":"/vasp-on-cluster/install-on-gpu-machine/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Installere VASP på GPU-maskin 
1) Installere Nvidia HPC SDK. Passe på at det er installert driver som passer med cuda-versjonen. F. eks 515 til cuda 11.7. Ser ut til å fungere med 11.0 på bigfacet. 
2) Installere environment-modules, og bruke /opt/nvidia.../modulefiles deretter module use nvhpc/XX.Y
3) Bruke arch/makefile.include.nvhpc_omp_acc og legge inn relevante baner (bare fftw3 tror jeg)
4) make DEPS=1 -j32
5) kopiere binaries til /usr/local/bin 