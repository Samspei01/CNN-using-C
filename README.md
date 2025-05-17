# CNN Implementation in C

This project implements a Convolutional Neural Network (CNN) in C for image classification using the CIFAR-10 dataset. The implementation focuses on performance optimization of the CNN forward pass.

## Overview

This CNN implementation consists of 11 layers including convolutional layers, ReLU activation layers, max pooling layers, fully connected layers, and softmax output. The network is designed to classify 10 different categories of images from the CIFAR-10 dataset.

## Project Structure

- **Core Implementation Files**:
  - `volume.h/c`: Implementation of the Volume data structure for storing and manipulating 3D data
  - `layers.h/c`: Implementation of different CNN layers (Conv, ReLU, Pool, FC, Softmax)
  - `network.h/c`: Implementation of the full CNN architecture
  - `benchmark.c`: Benchmarking and testing functionality

- **Baseline Implementations** (for performance comparison):
  - `volume_baseline.c`
  - `layers_baseline.c`
  - `network_baseline.c`

- **Test and Verification**:
  - `run_test.sh`: Script to run tests for correctness
  - `huge_test.sh`: Script to run larger tests
  - `test/`: Contains test files and reference outputs
  - `snapshot/`: Contains layer-wise input/output data for verification

## Building the Project

```bash
# Build the optimized implementation
make

# Build the baseline implementation for comparison
make baseline

# Build both and compare performance
make compare
```

## Running Tests

```bash
# Run correctness tests
./run_test.sh

# Run larger performance tests
./huge_test.sh
```

## Implementation Details

1. **Volume**: The fundamental data structure that represents a 3D volume of data.

2. **Layers**:
   - **Convolutional Layer**: Applies filters to the input volume
   - **ReLU Layer**: Applies the ReLU activation function
   - **Pool Layer**: Performs max pooling for downsampling
   - **FC Layer**: Fully connected layer
   - **Softmax Layer**: Outputs class probabilities

3. **Network**: Defines the architecture of the CNN with 11 layers

## Performance Optimization

This implementation focuses on optimizing the forward pass of the CNN. Optimizations may include:
- Loop restructuring
- OpenMP parallelization
- SIMD instructions via compiler optimizations
- Cache-friendly data access patterns

## Requirements

- C compiler with C99 support
- OpenMP support (for parallelization)
- CIFAR-10 dataset (referenced in benchmark.c)

## CIFAR-10 Dataset

The CIFAR-10 dataset consists of 60,000 32x32 color images in 10 classes, with 6,000 images per class. The classes are:
- Airplane
- Automobile
- Bird
- Cat
- Deer
- Dog
- Frog
- Horse
- Ship
- Truck

The dataset is divided into 50,000 training images and 10,000 testing images. This project uses the binary version of the dataset which can be found at:
```
/home/ff/cs61c/proj4/cifar-10-batches-bin
```
as referenced in the benchmark.c file.

## Benchmarking

The project includes benchmarking functionality to compare the performance of the optimized implementation against the baseline. The benchmark measures the time taken to perform forward passes on a set of images.

```bash
./benchmark [number_of_images]
```

By default, the benchmark runs on 1200 images if no arguments are provided.

## Contributing

If you would like to contribute to this project, please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Make your changes
4. Run tests to ensure correctness (`./run_test.sh`)
5. Commit your changes (`git commit -m 'Add some feature'`)
6. Push to the branch (`git push origin feature/your-feature`)
7. Create a new Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Thanks to the CIFAR-10 dataset creators for providing the data
- CS 61C course staff for the project structure and testing framework