# Caravel User Project

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![UPRJ_CI](https://github.com/efabless/caravel_project_example/actions/workflows/user_project_ci.yml/badge.svg)](https://github.com/efabless/caravel_project_example/actions/workflows/user_project_ci.yml) [![Caravel Build](https://github.com/efabless/caravel_project_example/actions/workflows/caravel_build.yml/badge.svg)](https://github.com/efabless/caravel_project_example/actions/workflows/caravel_build.yml)

| :exclamation: Important Note            |
|-----------------------------------------|



The Dynamically Adaptive Accumulator is designed for optimal performance in neural network accelerators. This innovative accumulator incorporates an adaptive accumulation algorithm,
ensuring that the multiplier results are dynamically adjusted to align with the fixed width of the adder.
This adaptive feature enhances the efficiency and precision of the accumulation process, making it well-suited for the complex computations involved in neural network acceleration.


DAA architecture
The DAA is composed of two main sections: (I) the multiplier section; (II) the accumulation section. 
The multiplier section is based on the radix-4 Booth algorithm to exploit an efficient multiplication. It is coupled with an the input partitioning of the other MAC input. This allows to operate a time splitting of the workload, with less inference time respect to a full-serial approach. In fact, an optimal trade-off between bit-serial and bit-decomposed approaches is achieved.
The accumulation section is based on an innovative algorithm: a monitoring of overflow and over-representation is executed at each accumulation cycle. According to which one occurs, the accumulation inputs are aligned to each other, keeping small the size of the accumulation adder. This approach enables to dynamically trade-off inputs uncertainty and computation accuracy, to achieve the required output precision. The main block of this section are: (I) pp aligner; (II) adder; (III) s-aligner;(IV) Control Unit (CU); (V) save LSB; (VI) sparse module. The pp aligner operates the alignment of the partial product produced by the multiplier section to the accumulated result (namely b), resulting in the adder input a. The s-aligner exploits the presented algorithm, using the signals of overflow and over-representation produced by the CU, on the result of the adder s, producing the adder input b. The save LSB section stores the truncated LSBs to mitigate the underflow. The sparse module allows to skip inputs equal to zero.

Main features
-Run-time reconfigurability;
-Novel MAC algorithm to avoid fixed-point destructive overflow;
-Sparse computing handling:
-up to 16-bit input activation and 8-bit input weight



## Please fill in your project documentation in this README.md file 

Refer to [README](docs/source/index.rst#section-quickstart) for a quickstart of how to use caravel_user_project

Refer to [README](docs/source/index.rst) for this sample project documentation. 

Refer to the following [readthedocs](https://caravel-sim-infrastructure.readthedocs.io/en/latest/index.html) for how to add cocotb tests to your project. 