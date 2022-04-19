Table Of Contents

[1. Getting Started Guide for MIGraphX](#1-getting-started-guide-for-migraphx)

[1.1. Introduction](#11-introduction)

[1.1.1. Documentation Roadmap](#documentation-roadmap)

[1.2. List of prerequisites](#12-list-of-prerequisites)

[1.3. Installing pre-built packages](#13-installing-pre-built-packages)

[1.4. Building From Source](#14-building-from-source)

[1.4.1. Use the ROCm build tool rbuild](#141-use-the-rocm-build-tool-rbuild)

[1.4.2. Use cmake to build MIGraphX](#142-use-cmake-to-build-migraphx)

[1.4.3. Use docker](#143-use-docker)

[2. Python User Guide](#2-python-user-guide)

[2.1. Setting path and installing package](#21-setting-path-and-installing-package)

[2.2 Defining different modules in detail](#22-defining-different-modules-in-detail)

[2.2.1. Shape](#221-shape)

[2.2.2. Argument](#222-argument)

[2.2.3. Target](#223-target)

[2.2.4. Program](#224-program)

[2.2.5. parse_onnx](#225-parse_onnx)

[2.2.6. parse_tf](#226-parse_tf)

[2.2.7. Load](#227-load)

[2.2.8. Save](#228-save)

[3. C++ User Guide](#3-c-user-guide)

[3.1 Defining different modules in detail](#31-defining-different-modules-in-detail)

[3.1.1 Shape](#311-shape)

[3.1.2 Argument](#312-argument)

[3.1.3 Target](#313-target)

[3.1.4 Program](#314-program)

[3.1.5 Quantize](#315-quantize)

[3.1.6 parse_onnx](#316-parse_onnx)

[3.1.7 Load](#317-load)

[3.1.8 Save](#318-save)

[4. MIGraphX Driver](#4-migraphx-driver)

[4.1 Description](#41-description)

[4.2 How to Use](#42-how-to-use)

[4.2.1 Commands](#421-commands)

[4.2.2 Options](#422-options)

[![Graphical user interface, application, email Description automatically generated](media/55968d31b828db50711928931e75d299.png)](#)

[4.3 Defining different modules in detail](#43-defining-different-modules-in-detail)

[4.3.1 Read](#431-read)

[4.3.2 compile](#432-compile)

[4.3.3 Run](#433-run)

[4.3.4 Perf](#434-perf)

[4.3.5 Verify](#435-verify)

[4.3.6 Roctx](#436-roctx)

[5. Contributor Guide](#5-contributor-guide)

[5.1 MIGraphX Fundamentals](#51-migraphx-fundamentals)

[5.1.1 Location of the Examples](#511-location-of-the-examples)

[5.1.2 Adding Two Literals](#512-adding-two-literals)

[5.1.3 Using Parameters](#513-using-parameters)

[5.1.4 Handling Tensor Data](#514-handling-tensor-data)

[5.1.5 Importing From ONNX](#515-importing-from-onnx)

**  
**

# 1. Getting Started Guide for MIGraphX

# 1.1. Introduction

The MIGraphX execution provider uses AMD's Deep Learning graph optimization engine to accelerate ONNX model on AMD GPUs.

ONNX Runtime is an accelerator for machine learning models with multi platform support and a flexible interface to integrate with hardware-specific libraries. ONNX Runtime can be used with models from PyTorch, Tensorflow/Keras, TFLite, scikit-learn, and other frameworks.

The document also contains an Python User guide, C++ user Guide, MIGraphX Driver and Contributor Guide.

## Documentation Roadmap

The following is a list of MIGraphX documents in the suggested reading order:

Getting Started Guide (this document): In this section we have introduce MIGraphX, ONNX Runtime.

Python User Guide: In this section we will be defining different modules like shape, target, argument, save, load, etc.

C++ Reference: Describe modules like shape, argument, load, parse_onnx, etc.

MIGraphX Driver: Under this section we will cover modules like perf, verify, roctx, etc.

Contributor’s Guide: Provides detailed information about MIGraphX Fundamentals, datatypes, operators, targets, etc.

# 1.2. List of prerequisites

The following is a list of prerequisites required to build MIGraphX source.

-   [ROCm cmake modules](https://github.com/RadeonOpenCompute/rocm-cmake) required
-   [MIOpen](https://github.com/ROCmSoftwarePlatform/MIOpen) for running on the GPU
-   [rocBLAS](https://github.com/ROCmSoftwarePlatform/rocBLAS) for running on the GPU
-   [HIP](https://github.com/ROCm-Developer-Tools/HIP) for running on the GPU
-   [Protobuf](https://github.com/google/protobuf) for reading [onnx](https://github.com/onnx/onnx) files
-   [Half](http://half.sourceforge.net/) - IEEE 754-based half-precision floating point library
-   [pybind11](https://pybind11.readthedocs.io/en/stable/) - for python bindings
-   [JSON](https://github.com/nlohmann/json) - for model serialization to json string format
-   [MessagePack](https://msgpack.org/index.html) - for model serialization to binary format

# 1.3. Installing pre-built packages

With ROCm installed correctly, MIGraphX binaries can be installed on Ubuntu with the following command:

sudo apt update && sudo apt install -y migraphx

then the header files and libs are installed under /opt/rocm-\<version\>, where \<version\> is the ROCm version.

# 1.4. Building From Source

There are three ways to build the MIGraphX sources.

-   [Use the ROCm build tool](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-the-rocm-build-tool-rbuild)

    This approach uses [rbuild](https://github.com/RadeonOpenCompute/rbuild) to install the prerequisites and build the libs with just one command.

-   [Use cmake](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-cmake-to-build-migraphx)

    This approach uses a script to install the prerequisites, then use cmake to build the source.

-   [Use docker](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-docker)

    This approach builds a docker image with all prerequisites installed, then build the MIGraphX sources inside a docker container.

#### **1.4.1. Use the ROCm build tool** [**rbuild**](https://github.com/RadeonOpenCompute/rbuild).

In this approach, we use the [rbuild](https://github.com/RadeonOpenCompute/rbuild) build tool to build MIGraphX. The specific steps are as follows:

1.  Install rocm-cmake, pip3, rocblas, and miopen-hip with the command

sudo apt update && sudo apt install -y rocm-cmake python3-pip rocblas miopen-hip

1.  Install [rbuild](https://github.com/RadeonOpenCompute/rbuild) (sudo may be required here.)

pip3 install https://github.com/RadeonOpenCompute/rbuild/archive/master.tar.gz

1.  Build MIGraphX source code

rbuild build -d depend -B build --cxx=/opt/rocm/llvm/bin/clang++

then all the prerequisites are in the folder depend, and MIGraphX is built in the build directory.

Note that for ROCm3.7 and later releases, Ubuntu 18.04 or later releases are needed. Upgrade to Ubuntu 18.04 is available at [Upgrade Ubuntu to 18.04](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/wiki/Upgrade-to-Ubuntu-18.04-for-ROCM3.7-or-later-releases)

Also note that you may meet the error of rbuild: command not found. It is because rbuild is installed at \$HOME/.local/bin, which is not in PATH. You can either export PATH as export PATH=\$HOME/.local/bin:\$PATH to add the folder to PATH or add the option --prefix /usr/local in the pip3 command when installing rbuild.

## 1.4.2. Use cmake to build MIGraphX

If using this approach, we need to install the prerequisites, configure the cmake, and then build the source.

##### Installing the prerequisites

For convenience, the prerequisites can be built automatically with rbuild as:

rbuild build -d depend --cxx=/opt/rocm/llvm/bin/clang++

then all the prerequisites are in the folder depend, and they can be used in the cmake configuration as -DCMAKE_PREFIX_PATH=depend.

If you have sudo access, as an alternative to the rbuild command, you can install the prerequisites just like in the dockerfile by calling ./tools/install_prereqs.sh.

(Note that this script is for Ubuntu. By default, all prerequisites are installed at the default location /usr/local and are accessible by all users. For the default location, sudo is required to run the script. You can also specify a location at which the prerequisites are installed with ./tools/install_prereqs.sh \$your_loc.)

##### Building MIGraphX source and install libs

With the above prerequisites installed, we can build source as:

1.  Go to the project folder and create a build directory:

mkdir build

cd build

1.  Configure the cmake. If the prerequisites are installed at the default location /usr/local, the command is:

CXX=/opt/rocm/llvm/bin/clang++ cmake..

Otherwise, you need to set -DCMAKE_PREFIX_PATH=\$your_loc to configure the cmake.

1.  Build MIGraphX source code

make -j\$(nproc)

Correctness can be verified as:

make -j\$(nproc) check

MIGraphX libs can be installed as:

make install

## 1.4.3. Use docker

The easiest way to setup the development environment is to use docker. With the dockerfile, you can build a docker image as:

docker build -t migraphx.

Then to enter the developement environment use docker run:

docker run --device='/dev/kfd' --device='/dev/dri' -v=\`pwd\`:/code/AMDMIGraphX -w /code/AMDMIGraphX --group-add video -it migraphx

In the docker container, all the required prerequisites are already installed, so users can just go to the folder /code/AMDMIGraphX and follow the steps in the above [Build MIGraphX source and install libs](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#building-migraphx-source-and-install-libs) section to build MIGraphX source.c

# 2. Python User Guide

# 2.1. Setting path and installing package

To use MIGraphX's Python module, please either set PYTHONPATH or use .deb package as explained below:

-   Setting PYTHONPATH:

export PYTHONPATH=/opt/rocm/lib:\$PYTHONPATH

-   Creating and installing the package:

To create deb package:

make package

This will provide the path of .deb package.

To install:

dpkg -i \<path_to_deb_file\>

# 2.2 Defining different modules in detail

## 2.2.1. Shape

**classmigraphx.shape(type**, **lens**, **strides=None)**

Describes the shape of a tensor. This includes size, layout, and data type/

**migraphx.type()**

An integer that represents the type

**Return type:** int

**migraphx.lens()**

A list of the lengths of the shape

**Return type:** list[int]

**migraphx.strides()**

A list of the strides of the shape

**Return type:** list[int]

**migraphx.elements()**

The number of elements in the shape

**Return type:** int

**migraphx.bytes()**

The number of bytes the shape uses

**Return type:** int

**migraphx.type_size()**

The number of bytes one element uses

**Return type:** int

**migraphx.packed()**

Returns true if the shape is packed.

**Return type:** bool

**migraphx.transposed()**

Returns true if the shape is transposed.

**Return type:** bool

**migraphx.broadcasted()**

Returns true if the shape is broadcasted.

**Return type:** bool

**migraphx.standard()**

Returns true if the shape is a standard shape. That is, the shape is both packed and not transposed.

**Return type:** bool

**migraphx.scalar()**

Returns true if all strides are equal to 0 (scalar tensor).

**Return type:** bool

## 2.2.2. Argument

**classmigraphx.argument(data)**

Construct an argument from a python buffer. This can include numpy arrays.

**migraphx.get_shape()**

Returns the shape of the argument.

**Return type:** shape

**migraphx.tolist()**

Convert the elements of the argument to a python list.

**Return type:** list

**migraphx.generate_argument(s**, **seed=0)**

Generate an argument with random data.

**Parameters: s** ([*shape*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.shape)) – Shape of argument to generate.

**seed** (*int*) – The seed used for random number generation

**Return type:** [argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)

## 2.2.3. Target

**Class migraphx.target**

This represents the compiliation target.

**migraphx.get_target(name)**

Constructs the target.

**Parameters: name** (*str*) – The name of the target to construct. This can either be ‘gpu’ or ‘ref’.

**Return type:** target

## 2.2.4. Program

**class migraphx.program**

Represents the computation graph to be compiled and run.

**migraphx.clone()**

Make a copy of the program

**Return type:** [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

**migraphx.get_parameter_shapes()**

Get the shapes of all the input parameters in the program.

**Return type:** dict[str, [shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.shape)]

**migraphx.get_shape()**

Get the shape of the final output of the program.

**Return type:** [shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.shape)

**migraphx.compile(t**, **offload_copy=True**, **fast_math=True)**

Compiles the program for the target and optimizes it.

**Parameters**

-   **t** ([*target*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.target)) – This is the target to compile the program for.
-   **offload_copy** (*bool*) – For targets with offloaded memory(such as the gpu), this will insert instructions during compilation to copy the input parameters to the offloaded memory and to copy the final result from the offloaded memory back to main memory.
-   **fast_math** (*bool*) – Optimize math functions to use faster approximate versions. There may be slight accuracy degredation when enabled.

**migraphx.run(params)**

Run the program.

**Parameters: params** (*dict[str,* [*argument*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)*]*) – This is a map of the input parameters which will be used when running the program.

**Returns:** The result of the last instruction.

**Return type:** [argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)

**migraphx.quantize_fp16(prog**, **ins_names=['all'])**

Quantize the program to use fp16.

**Parameters: prog** ([*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)) – Program to quantize.

**ins_names** (*list[str]*) – List of instructions to quantize.

**migraphx.quantize_int8(prog**, **t**, **calibration=[]**, **ins_names=['dot', 'convolution'])**

Quantize the program to use int8.

**Parameters**

-   **prog** ([*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)) – Program to quantize.
-   **t** ([*target*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.target)) – Target that will be used to run the calibration data.
-   **calibration** (*list[dict[str,* [*argument*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)*]]*) – Calibration data used to decide the parameters to the int8 optimization.
-   **ins_names** (*list[str]*) – List of instructions to quantize.

## 2.2.5. parse_onnx

migraphx.parse_onnx(filename, default_dim_value=1, map_input_dims={}, skip_unknown_operators=false, print_program_on_error=false)

Load and parse an onnx file.

**Parameters**

-   **filename** (*str*) – Path to file.
-   **default_dim_value** (*str*) – default batch size to use (if not specified in onnx file).
-   **map_input_dims** (*str*) – Explicitly specify the dims of an input.
-   **skip_unknown_operators** (*str*) – Continue parsing onnx file if an unknown operator is found.
-   **print_program_on_error** (*str*) – Print program if an error occurs.

    **Return type:** [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

## 2.2.6. parse_tf

**migraphx.parse_tf(filename**, **is_nhwc=True**, **batch_size=1)**

Load and parse an tensorflow protobuf file file.

**Parameters**

-   **filename** (*str*) – Path to file.
-   **is_nhwc** (*bool*) – Use nhwc as default format.
-   **batch_size** (*str*) – default batch size to use (if not specified in protobuf).

    **Return type:** [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

## 2.2.7. Load

**migraphx.load(filename**, **format='msgpack')**

Load a MIGraphX program

**Parameters**

-   **filename** (*str*) – Path to file.
-   **format** (*str*) – Format of file. Valid options are msgpack or json.

**Return type:** [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

## 2.2.8. Save

**migraphx.save(p**, **filename**, **format='msgpack')**

Save a MIGraphX program

**Parameters**

-   **p** ([*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)) – Program to save.
-   **filename** (*str*) – Path to file.
-   **format** (*str*) – Format of file. Valid options are msgpack or json.

# 3. C++ User Guide

# 3.1 Defining different modules in detail

## 3.1.1 Shape

**enum migraphx_shape_datatype_t**

An enum to represent the different data type inputs.

*Values:*

**enumerator migraphx_shape_tuple_type**

**enumerator migraphx_shape_bool_type**

**enumerator migraphx_shape_half_type**

**enumerator migraphx_shape_float_type**

**enumerator migraphx_shape_double_type**

**enumerator migraphx_shape_uint8_type**

**enumerator migraphx_shape_int8_type**

**enumerator migraphx_shape_uint16_type**

**enumerator migraphx_shape_int16_type**

**enumerator migraphx_shape_int32_type**

**enumerator migraphx_shape_int64_type**

**enumerator migraphx_shape_uint32_type**

**enumerator migraphx_shape_uint64_type**

# 

**struct migraphx::shape : public migraphx::handle_base\<\>**

Describe shape of tensor.

A shape consists of a data type, lengths of multi-dimension tensor, and strides

**Public Functions**

**inline shape()**

**inline shape(const migraphx_shape \*p)**

**inline shape(migraphx_shape \*p**, **own)**

**inline shape(migraphx_shape \*p**, **borrow)**

**inline shape(**[**migraphx_shape_datatype_t**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv425migraphx_shape_datatype_t) **type)**

Construct a scalar shape.

**inline shape(**[**migraphx_shape_datatype_t**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv425migraphx_shape_datatype_t) **type, std::vector\<size_t\> plengths)**

Construct a shape with its type and lengths. The strides are automatically computed assumming a packed layout.

## 3.1.2 Argument

**struct migraphx::argument : public migraphx::handle_base\<\>**

Arguments to be passed to an migraphx arguments.

An argument represents a raw buffer of data with a shape.

**Public Functions**

**inline argument()**

**inline argument(migraphx_argument \*p**, **borrow)**

**inline argument(migraphx_argument \*p**, **own)**

**inline argument(const migraphx_argument \*p)**

**inline argument(**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) **pshape, void \*pbuffer)**

**inline** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) **get_shape() const**

**inline char \*data() const**

Public Static Functions

**static inline** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) **generate(**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) **ps, size_t pseed = 0)**

Generate an argument using random data.

**Friends**

**inline** **friend** **friend** **bool** **operator==** **(const** **argument** **\&px,** **const** **argument** **\&py)**

**inline** **friend** **friend** **bool** **operator!=** **(const** **argument** **\&px,** **const** **argument** **\&py)**

## 3.1.3 Target

**struct migraphx::target : public migraphx::handle_base\<\>**

A

target for compilation.

**Public Functions**

**inline target()**

**inline target(migraphx_target \*p**, **own)**

**inline target(migraphx_target \*p**, **borrow)**

**inline target(const char \*name)**

Construct a target from its name.

## 3.1.4 Program

**struct migraphx::program_parameter_shapes : public migraphx::handle_base\<\>**

Public Functions

**inline program_parameter_shapes()**

**inline program_parameter_shapes(migraphx_program_parameter_shapes \*p**, **own)**

**inline program_parameter_shapes(migraphx_program_parameter_shapes \*p**, **borrow)**

**inline size_t size() const**

**inline** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) **operator[](const char \*pname) const**

**inline std::vector\<const char\*\> names() const**

**struct migraphx::program_parameters : public migraphx::handle_base\<\>**

A class to construct the inputs parameters for a program.

**Public Functions**

**inline program_parameters(migraphx_program_parameters \*p**, **own)**

**inline program_parameters(migraphx_program_parameters \*p**, **borrow)**

**inline program_parameters(migraphx_program_parameters \*p)**

**inline program_parameters()inline program_parameters(std::initializer_list\<std::pair\<std::string,** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE)**\>\> l)**

Construct the parameters from initializer_list.

**inline void add(const char \*pname, const** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) **\&pargument) const**

Add a new parameter.

**struct migraphx_compile_options**

**Public Functions**

**template\<class ...Ts\>  
inline migraphx_compile_options(**[**Ts**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4IDpEN24migraphx_compile_options24migraphx_compile_optionsEDpRR2Ts)**&&... xs)**

**Public Members**

**migraphx::compile_options object**

**struct migraphx::program : public migraphx::handle_base\<\>**

A program represents the all computation graphs to be compiled and executed.

**Public Functions**

**inline program()**

**inline program(migraphx_program \*p**, **own)**

**inline program(migraphx_program \*p**, **borrow)**

**inline void compile(const** [**target**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx6targetE) **\&ptarget, const compile_options \&poptions) const**

Compile the program for a specific target to be ran on.

**inline void compile(const** [**target**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx6targetE) **\&ptarget) const**

Compile the program for a specific target to be ran on.

**inline** [**program_parameter_shapes**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx24program_parameter_shapesE) **get_parameter_shapes() const**

Return the shapes for the input parameters.

**inline shapes get_output_shapes() const**

Get the shapes of all the outputs returned by this program.

**inline arguments eval(const** [**program_parameters**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx18program_parametersE) **\&pparams) const**

Run the program using the inputs passed in.

**inline void print() const**

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **sort()**

**inline module get_main_module()**

**Friends**

**inline** **friend** **friend** **bool** **operator==** **(const** **program** **\&px,** **const** **program** **\&py)**

**inline** **friend** **friend** **bool** **operator!=** **(const** **program** **\&px,** **const** **program** **\&py)**

## 3.1.5 Quantize

**struct migraphx::quantize_op_names : public migraphx::handle_base\<\>**

**Public Functions**

**inline quantize_op_names()**

**inline quantize_op_names(migraphx_quantize_op_names \*p**, **own)**

**inline void add(const std::string \&name)**

**inline void migraphx::quantize_fp16(const** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **\&prog)**

Quantize program to use fp16.

**inline void migraphx::quantize_fp16(const** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **\&prog, const** [**quantize_op_names**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx17quantize_op_namesE) **\&names)**

Quantize program to use fp16.

**struct migraphx::quantize_int8_options : public migraphx::handle_base\<\>**

Options to be passed when quantizing for int8.

**Public Functions**

**inline quantize_int8_options()**

**inline quantize_int8_options(migraphx_quantize_int8_options \*p**, **own)**

**inline quantize_int8_options(migraphx_quantize_int8_options \*p**, **borrow)**

**inline void add_op_name(const std::string \&name)**

Add an operator that should be quantized.

**inline void add_calibration_data(const** [**program_parameters**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx18program_parametersE) **\&pp)**

Add calibrartion data to be used for quantizing.

**Public Members**

**std::vector\<parameter_map\> calibration = {}**

**std::vector\<std::string\> op_names = {}**

**inline void migraphx::quantize_int8(const** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **\&prog, const** [**target**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx6targetE) **\&ptarget, const** [**quantize_int8_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx21quantize_int8_optionsE) **\&options)**

Quantize program to use int8.

## 3.1.6 parse_onnx

**struct migraphx::onnx_options : public migraphx::handle_base\<\>**

Options for parsing onnx options.

**Public Functions**

**inline onnx_options()**

**inline onnx_options(migraphx_onnx_options \*p**, **own)**

**inline void set_input_parameter_shape(const std::string \&name**, **std::vector\<std::size_t\> dim)**

Make onnx parser treat an inputs with a certain dimensions.

**inline void set_default_dim_value(unsigned int value)**

When there is a dimension parameter, then use this default value.

**inline void set_default_loop_iterations(int64_t value)**

Set default max iteration number for the loop operator.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx(const char \*filename)**

Parse an onnx file into a migraphx program.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx(const char \*filename, const migraphx::**[**onnx_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx12onnx_optionsE) **\&options)**

Parse an onnx file into a migraphx program.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const std::string \&buffer)**

Parse a buffer of memory as an onnx file.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const std::string \&buffer, const migraphx::**[**onnx_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx12onnx_optionsE) **\&options)**

Parse a buffer of memory as an onnx file.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const void \*data, size_t size)**

Parse a buffer of memory as an onnx file.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const void \*data, size_t size, const migraphx::**[**onnx_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx12onnx_optionsE) **\&options)**

Parse a buffer of memory as an onnx file.

## 3.1.7 Load

**struct migraphx_file_options**

**Public Functions**

**template\<class ...Ts\>  
inline migraphx_file_options(**[**Ts**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4IDpEN21migraphx_file_options21migraphx_file_optionsEDpRR2Ts)**&&... xs)**

**Public Members**

**migraphx::file_options object**

Load a saved migraphx program from a file.

## 3.1.8 Save

**inline void migraphx::save(const** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **\&p, const char \*filename)**

Save a program to a file.

# 4. MIGraphX Driver

# 4.1 Description

The MIGraphX driver is a tool that allows you to utilize many of the core functions of MIGraphX without having to write your own program.

# 4.2 How to Use

The MIGraphX driver is installed with MIGraphX and can be found in */opt/rocm/bin/migraphx-driver*, or in *AMDMIGraphX/build/bin/migraphx-driver* after building the source code.

See below for a comprehensive list of commands and option arguments, as well as some usage examples.

## 4.2.1 Commands

## 

![Graphical user interface, text, application, email Description automatically generated](media/19520c77695364dfd7eed063ccad316c.png)

## 4.2.2 Options

## 

## ![Graphical user interface, application, email Description automatically generated](media/55968d31b828db50711928931e75d299.png)

# 

# 4.3 Defining different modules in detail

## 4.3.1 Read

Loads and prints input graph.

**\<input file\>**

File to load

**--model [resnet50\|inceptionv3\|alexnet]**

Load model

\--onnx

Load as onnx

\--tf

Load as tensorflow

\--migraphx

Load as MIGraphX

\--migraphx-json

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1)

Set batch size for model

\--nhwc

Treat tensorflow format as nhwc

\--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

\--nchw

Treat tensorflow format as nchw

\--trim, -t [unsigned int]

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>]

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O

Optimize when reading

\--graphviz, -g

Print out a graphviz representation.

\--brief

Make the output brief.

\--cpp

Print out the program as cpp program.

\--json

Print out program as json.

\--text

Print out program in text format.

\--binary

Print out program in binary format.

\--output, -o [std::string]

Output to file.

## 4.3.2 compile

Compiles and prints input graph.

\<input file\>

File to load

\--model [resnet50\|inceptionv3\|alexnet]

Load model

\--onnx

Load as onnx

\--tf

Load as tensorflow

\--migraphx

Load as MIGraphX

\--migraphx-json

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1)

Set batch size for model

\--nhwc

Treat tensorflow format as nhwc

\--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

\--nchw

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-int8>

Quantize for int8

## 4.3.3 Run

Loads and prints input graph.

\<input file\> <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-arg-input>

File to load

\--model [resnet50\|inceptionv3\|alexnet] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-model>

Load model

\--onnx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-onnx>

Load as onnx

\--tf <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-tf>

Load as tensorflow

\--migraphx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-migraphx>

Load as MIGraphX

\--migraphx-json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-migraphx-json>

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-batch>

Set batch size for model

\--nhwc <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-nhwc>

Treat tensorflow format as nhwc

\--skip-unknown-operators <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-skip-unknown-operators>

Skip unknown operators when parsing and continue to parse.

\--nchw <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-nchw>

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-int8>

Quantize for int8

## 4.3.4 Perf

Compiles and runs input graph then prints performance report.

\<input file\> <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-arg-input>

File to load

\--model [resnet50\|inceptionv3\|alexnet] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-model>

Load model

\--onnx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-onnx>

Load as onnx

\--tf <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-tf>

Load as tensorflow

\--migraphx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-migraphx>

Load as MIGraphX

\--migraphx-json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-migraphx-json>

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-batch>

Set batch size for model

\--nhwc <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-nhwc>

Treat tensorflow format as nhwc

\--skip-unknown-operators <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-skip-unknown-operators>

Skip unknown operators when parsing and continue to parse.

\--nchw <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-nchw>

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-int8>

Quantize for int8

\--iterations, -n [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-iterations>

Number of iterations to run for perf report (Default: 100)

## 4.3.5 Verify

Runs reference and CPU or GPU implementations and checks outputs for consistency.

\<input file\> <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-arg-input>

File to load

\--model [resnet50\|inceptionv3\|alexnet] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-model>

Load model

\--onnx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-onnx>

Load as onnx

\--tf <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-tf>

Load as tensorflow

\--migraphx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-migraphx>

Load as MIGraphX

\--migraphx-json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-migraphx-json>

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-batch>

Set batch size for model

\--nhwc <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-nhwc>

Treat tensorflow format as nhwc

\--skip-unknown-operators <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-skip-unknown-operators>

Skip unknown operators when parsing and continue to parse.

\--nchw <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-nchw>

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-int8>

Quantize for int8

\--tolerance [double] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-tolerance>

Tolerance for errors (Default: 80)

\-i, --per-instruction <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-i>

Verify each instruction

\-r, --reduce <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-r>

Reduce program and verify

## 4.3.6 Roctx

Provides marker information for each operation, allowing MIGraphX to be used with [rocprof](https://rocmdocs.amd.com/en/latest/ROCm_Tools/ROCm-Tools.html) for performance analysis. This allows user to get GPU-level kernel timing information. An example command line combined with rocprof for tracing purposes is given below:

/opt/rocm/bin/rocprof --hip-trace --roctx-trace --flush-rate 1ms --timestamp on -d \<OUTPUT_PATH\> --obj-tracking on /opt/rocm/bin/migraphx-driver roctx \<ONNX_FILE\> \<MIGRAPHX_OPTIONS\>

After **rocprof** is run, the output directory will contain trace information for HIP, HCC and ROCTX in seperate **.txt** files. To understand the interactions between API calls, it is recommended to utilize **roctx.py** helper script as desribed in dev/tools:rocTX section.

\<input file\> <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-arg-input>

File to load

\--model [resnet50\|inceptionv3\|alexnet] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-model>

Load model

\--onnx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-onnx>

Load as onnx

\--tf <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-tf>

Load as tensorflow

\--migraphx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-migraphx>

Load as MIGraphX

\--migraphx-json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-migraphx-json>

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-batch>

Set batch size for model

\--nhwc <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-nhwc>

Treat tensorflow format as nhwc

\--skip-unknown-operators <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-skip-unknown-operators>

Skip unknown operators when parsing and continue to parse.

\--nchw <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-nchw>

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-int8>

Quantize for int8

# 5. Contributor Guide

# 5.1 MIGraphX Fundamentals

MIGraphX provides an optimized execution engine for deep learning neural networks. We will cover some simple operations in the MIGraphX framework here. For a quick start guide to using MIGraphX, look in the example directory:

https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/tree/develop/examples/migraphx.

## 5.1.1 Location of the Examples

The ref_dev_examples.cpp can be found in the test directory (/test). The executable file test_ref_dev_examples based on this file will be created in the bin/ of the build directory after running make -j\$(nproc) test_ref_dev_examples. The executable will also be created when running make -j\$(nproc) check, alongside with all the other tests. Directions for building MIGraphX from source can be found in the main README file:

[https://github.com/ROCmSoftwarePlatform/AMDMIGraphX\#readme](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#readme).

## 5.1.2 Adding Two Literals

A program is a collection of modules, which are collections of instructions to be executed when calling [**eval**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4NK8migraphx7program4evalERK18program_parameters). Each instruction has an associated **operation** which represents the computation to be performed by the instruction.

We start with a snippet of the simple add_two_literals() function:

*// create the program and get a pointer to the main module*

migraphx::program p;

**auto**\* mm = p.get_main_module();

*// add two literals to the program*

**auto** one = mm-\>add_literal(1);

**auto** two = mm-\>add_literal(2);

*// make the add operation between the two literals and add it to the program*

mm-\>add_instruction(migraphx::make_op("add"), one, two);

*// compile the program on the reference device*

p.compile(migraphx::ref::target{});

*// evaulate the program and retreive the result*

**auto** result = p.eval({}).back();

std::cout \<\< "add_two_literals: 1 + 2 = " \<\< result \<\< "**\\n**";

We start by creating a simple migraphx::program object and then getting a pointer to the main module of it. The program is a collection of modules that start executing from the main module, so instructions are added to the modules rather than directly onto the program object. We then use the **add_literal** function to add an instruction that stores the literal number 1 while returning an **instruction_ref**. The returned **instruction_ref** can be used in another instruction as an input. We use the same **add_literal** function to add a 2 to the program. After creating the literals, we then create the instruction to add the numbers together. This is done by using the **add_instruction** function with the "add" **operation** created by **make_op** along with the previous **add_literal** **instruction_ref** for the input arguments of the instruction. Finally, we can run this [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) by compiling it for the reference target (CPU) and then running it with [**eval**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4NK8migraphx7program4evalERK18program_parameters) The result is then retreived and printed to the console.

We can compile the program for the GPU as well, but the file will have to be moved to the test/gpu/ directory and the correct target must be included:

\#include *\<migraphx/gpu/target.hpp\>*

## 

## 5.1.3 Using Parameters

The previous program will always produce the same value of adding 1 and 2. In the next program we want to pass an input to a program and compute a value based on the input. We can modify the program to take an input parameter x, as seen in the add_parameter() function:

migraphx::program p;

**auto**\* mm = p.get_main_module();

migraphx::shape s{migraphx::shape::int32_type, {1}};

*// add a "x" parameter with the shape s*

**auto** x = mm-\>add_parameter("x", s);

**auto** two = mm-\>add_literal(2);

*// add the "add" instruction between the "x" parameter and "two" to the module*

mm-\>add_instruction(migraphx::make_op("add"), x, two);

p.compile(migraphx::ref::target{});

This adds a parameter of type int32, and compiles it for the CPU. To run the program, we need to pass the parameter as a parameter_map when we call [**eval**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4NK8migraphx7program4evalERK18program_parameters). We create the parameter_map by setting the x key to an [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) object with an int data type:

*// create a parameter_map object for passing a value to the "x" parameter*

std::vector\<int\> data = {4};

migraphx::parameter_map params;

params["x"] = migraphx::argument(s, data.data());

**auto** result = p.eval(params).back();

std::cout \<\< "add_parameters: 4 + 2 = " \<\< result \<\< "**\\n**";

EXPECT(result.at\<int\>() == 6);

## 

## 5.1.4 Handling Tensor Data

In the previous examples we have only been dealing with scalars, but the [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) class can describe multi-dimensional tensors. For example, we can compute a simple convolution:

migraphx::program p;

**auto**\* mm = p.get_main_module();

*// create shape objects for the input tensor and weights*

migraphx::shape input_shape{migraphx::shape::float_type, {2, 3, 4, 4}};

migraphx::shape weights_shape{migraphx::shape::float_type, {3, 3, 3, 3}};

*// create the parameters and add the "convolution" operation to the module*

**auto** input = mm-\>add_parameter("X", input_shape);

**auto** weights = mm-\>add_parameter("W", weights_shape);

mm-\>add_instruction(migraphx::make_op("convolution", {{"padding", {1, 1}}, {"stride", {2, 2}}}), input, weights);

Here we create two parameters for both the input and weights. In the previous examples, we created simple literals, however, most programs will take data from allocated buffers (usually on the GPU). In this case, we can create [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) objects directly from the pointers to the buffers:

*// Compile the program*

p.compile(migraphx::ref::target{});

*// Allocated buffers by the user*

std::vector\<float\> a = ...;

std::vector\<float\> c = ...;

*// Solution vector*

std::vector\<float\> sol = ...;

*// Create the arguments in a parameter_map*

migraphx::parameter_map params;

params["X"] = migraphx::argument(input_shape, a.data());

params["W"] = migraphx::argument(weights_shape, c.data());

*// Evaluate and confirm the result*

**auto** result = p.eval(params).back();

std::vector\<float\> results_vector(64);

result.visit([&](**auto** output) { results_vector.assign(output.begin(), output.end()); });

EXPECT(migraphx::verify_range(results_vector, sol));

An [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) can handle memory buffers from either the GPU or the CPU. By default when running the [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE), buffers are allocated on the corresponding target. When compiling for the CPU, the buffers by default will be allocated on the CPU. When compiling for the GPU, the buffers by default will be allocated on the GPU. With the option offloaf_copy=true set while compiling for the GPU, the buffers will be located on the CPU.

## 5.1.5 Importing From ONNX

A [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) can be built directly from an onnx file using the MIGraphX ONNX parser. This makes it easier to use neural networks directly from other frameworks. In this case, there is an parse_onnx function:

program p = migraphx::parse_onnx("model.onnx");

p.compile(migraphx::gpu::target{});

# 

Table Of Contents

[1. Getting Started Guide for MIGraphX](#1-getting-started-guide-for-migraphx)

[1.1. Introduction](#11-introduction)

[1.1.1. Documentation Roadmap](#documentation-roadmap)

[1.2. List of prerequisites](#12-list-of-prerequisites)

[1.3. Installing pre-built packages](#13-installing-pre-built-packages)

[1.4. Building From Source](#14-building-from-source)

[1.4.1. Use the ROCm build tool rbuild](#141-use-the-rocm-build-tool-rbuild)

[1.4.2. Use cmake to build MIGraphX](#142-use-cmake-to-build-migraphx)

[1.4.3. Use docker](#143-use-docker)

[2. Python User Guide](#2-python-user-guide)

[2.1. Setting path and installing package](#21-setting-path-and-installing-package)

[2.2 Defining different modules in detail](#22-defining-different-modules-in-detail)

[2.2.1. Shape](#221-shape)

[2.2.2. Argument](#222-argument)

[2.2.3. Target](#223-target)

[2.2.4. Program](#224-program)

[2.2.5. parse_onnx](#225-parse_onnx)

[2.2.6. parse_tf](#226-parse_tf)

[2.2.7. Load](#227-load)

[2.2.8. Save](#228-save)

[3. C++ User Guide](#3-c-user-guide)

[3.1 Defining different modules in detail](#31-defining-different-modules-in-detail)

[3.1.1 Shape](#311-shape)

[3.1.2 Argument](#312-argument)

[3.1.3 Target](#313-target)

[3.1.4 Program](#314-program)

[3.1.5 Quantize](#315-quantize)

[3.1.6 parse_onnx](#316-parse_onnx)

[3.1.7 Load](#317-load)

[3.1.8 Save](#318-save)

[4. MIGraphX Driver](#4-migraphx-driver)

[4.1 Description](#41-description)

[4.2 How to Use](#42-how-to-use)

[4.2.1 Commands](#421-commands)

[4.2.2 Options](#422-options)

[![Graphical user interface, application, email Description automatically generated](media/55968d31b828db50711928931e75d299.png)](#)

[4.3 Defining different modules in detail](#43-defining-different-modules-in-detail)

[4.3.1 Read](#431-read)

[4.3.2 compile](#432-compile)

[4.3.3 Run](#433-run)

[4.3.4 Perf](#434-perf)

[4.3.5 Verify](#435-verify)

[4.3.6 Roctx](#436-roctx)

[5. Contributor Guide](#5-contributor-guide)

[5.1 MIGraphX Fundamentals](#51-migraphx-fundamentals)

[5.1.1 Location of the Examples](#511-location-of-the-examples)

[5.1.2 Adding Two Literals](#512-adding-two-literals)

[5.1.3 Using Parameters](#513-using-parameters)

[5.1.4 Handling Tensor Data](#514-handling-tensor-data)

[5.1.5 Importing From ONNX](#515-importing-from-onnx)

**  
**

# 1. Getting Started Guide for MIGraphX

# 1.1. Introduction

The MIGraphX execution provider uses AMD's Deep Learning graph optimization engine to accelerate ONNX model on AMD GPUs.

ONNX Runtime is an accelerator for machine learning models with multi platform support and a flexible interface to integrate with hardware-specific libraries. ONNX Runtime can be used with models from PyTorch, Tensorflow/Keras, TFLite, scikit-learn, and other frameworks.

The document also contains an Python User guide, C++ user Guide, MIGraphX Driver and Contributor Guide.

## Documentation Roadmap

The following is a list of MIGraphX documents in the suggested reading order:

Getting Started Guide (this document): In this section we have introduce MIGraphX, ONNX Runtime.

Python User Guide: In this section we will be defining different modules like shape, target, argument, save, load, etc.

C++ Reference: Describe modules like shape, argument, load, parse_onnx, etc.

MIGraphX Driver: Under this section we will cover modules like perf, verify, roctx, etc.

Contributor’s Guide: Provides detailed information about MIGraphX Fundamentals, datatypes, operators, targets, etc.

# 1.2. List of prerequisites

The following is a list of prerequisites required to build MIGraphX source.

-   [ROCm cmake modules](https://github.com/RadeonOpenCompute/rocm-cmake) required
-   [MIOpen](https://github.com/ROCmSoftwarePlatform/MIOpen) for running on the GPU
-   [rocBLAS](https://github.com/ROCmSoftwarePlatform/rocBLAS) for running on the GPU
-   [HIP](https://github.com/ROCm-Developer-Tools/HIP) for running on the GPU
-   [Protobuf](https://github.com/google/protobuf) for reading [onnx](https://github.com/onnx/onnx) files
-   [Half](http://half.sourceforge.net/) - IEEE 754-based half-precision floating point library
-   [pybind11](https://pybind11.readthedocs.io/en/stable/) - for python bindings
-   [JSON](https://github.com/nlohmann/json) - for model serialization to json string format
-   [MessagePack](https://msgpack.org/index.html) - for model serialization to binary format

# 1.3. Installing pre-built packages

With ROCm installed correctly, MIGraphX binaries can be installed on Ubuntu with the following command:

sudo apt update && sudo apt install -y migraphx

then the header files and libs are installed under /opt/rocm-\<version\>, where \<version\> is the ROCm version.

# 1.4. Building From Source

There are three ways to build the MIGraphX sources.

-   [Use the ROCm build tool](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-the-rocm-build-tool-rbuild)

    This approach uses [rbuild](https://github.com/RadeonOpenCompute/rbuild) to install the prerequisites and build the libs with just one command.

-   [Use cmake](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-cmake-to-build-migraphx)

    This approach uses a script to install the prerequisites, then use cmake to build the source.

-   [Use docker](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-docker)

    This approach builds a docker image with all prerequisites installed, then build the MIGraphX sources inside a docker container.

#### **1.4.1. Use the ROCm build tool** [**rbuild**](https://github.com/RadeonOpenCompute/rbuild).

In this approach, we use the [rbuild](https://github.com/RadeonOpenCompute/rbuild) build tool to build MIGraphX. The specific steps are as follows:

1.  Install rocm-cmake, pip3, rocblas, and miopen-hip with the command

sudo apt update && sudo apt install -y rocm-cmake python3-pip rocblas miopen-hip

1.  Install [rbuild](https://github.com/RadeonOpenCompute/rbuild) (sudo may be required here.)

pip3 install https://github.com/RadeonOpenCompute/rbuild/archive/master.tar.gz

1.  Build MIGraphX source code

rbuild build -d depend -B build --cxx=/opt/rocm/llvm/bin/clang++

then all the prerequisites are in the folder depend, and MIGraphX is built in the build directory.

Note that for ROCm3.7 and later releases, Ubuntu 18.04 or later releases are needed. Upgrade to Ubuntu 18.04 is available at [Upgrade Ubuntu to 18.04](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/wiki/Upgrade-to-Ubuntu-18.04-for-ROCM3.7-or-later-releases)

Also note that you may meet the error of rbuild: command not found. It is because rbuild is installed at \$HOME/.local/bin, which is not in PATH. You can either export PATH as export PATH=\$HOME/.local/bin:\$PATH to add the folder to PATH or add the option --prefix /usr/local in the pip3 command when installing rbuild.

## 1.4.2. Use cmake to build MIGraphX

If using this approach, we need to install the prerequisites, configure the cmake, and then build the source.

##### Installing the prerequisites

For convenience, the prerequisites can be built automatically with rbuild as:

rbuild build -d depend --cxx=/opt/rocm/llvm/bin/clang++

then all the prerequisites are in the folder depend, and they can be used in the cmake configuration as -DCMAKE_PREFIX_PATH=depend.

If you have sudo access, as an alternative to the rbuild command, you can install the prerequisites just like in the dockerfile by calling ./tools/install_prereqs.sh.

(Note that this script is for Ubuntu. By default, all prerequisites are installed at the default location /usr/local and are accessible by all users. For the default location, sudo is required to run the script. You can also specify a location at which the prerequisites are installed with ./tools/install_prereqs.sh \$your_loc.)

##### Building MIGraphX source and install libs

With the above prerequisites installed, we can build source as:

1.  Go to the project folder and create a build directory:

mkdir build

cd build

1.  Configure the cmake. If the prerequisites are installed at the default location /usr/local, the command is:

CXX=/opt/rocm/llvm/bin/clang++ cmake..

Otherwise, you need to set -DCMAKE_PREFIX_PATH=\$your_loc to configure the cmake.

1.  Build MIGraphX source code

make -j\$(nproc)

Correctness can be verified as:

make -j\$(nproc) check

MIGraphX libs can be installed as:

make install

## 1.4.3. Use docker

The easiest way to setup the development environment is to use docker. With the dockerfile, you can build a docker image as:

docker build -t migraphx.

Then to enter the developement environment use docker run:

docker run --device='/dev/kfd' --device='/dev/dri' -v=\`pwd\`:/code/AMDMIGraphX -w /code/AMDMIGraphX --group-add video -it migraphx

In the docker container, all the required prerequisites are already installed, so users can just go to the folder /code/AMDMIGraphX and follow the steps in the above [Build MIGraphX source and install libs](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#building-migraphx-source-and-install-libs) section to build MIGraphX source.c

# 2. Python User Guide

# 2.1. Setting path and installing package

To use MIGraphX's Python module, please either set PYTHONPATH or use .deb package as explained below:

-   Setting PYTHONPATH:

export PYTHONPATH=/opt/rocm/lib:\$PYTHONPATH

-   Creating and installing the package:

To create deb package:

make package

This will provide the path of .deb package.

To install:

dpkg -i \<path_to_deb_file\>

# 2.2 Defining different modules in detail

## 2.2.1. Shape

**classmigraphx.shape(type**, **lens**, **strides=None)**

Describes the shape of a tensor. This includes size, layout, and data type/

**migraphx.type()**

An integer that represents the type

**Return type:** int

**migraphx.lens()**

A list of the lengths of the shape

**Return type:** list[int]

**migraphx.strides()**

A list of the strides of the shape

**Return type:** list[int]

**migraphx.elements()**

The number of elements in the shape

**Return type:** int

**migraphx.bytes()**

The number of bytes the shape uses

**Return type:** int

**migraphx.type_size()**

The number of bytes one element uses

**Return type:** int

**migraphx.packed()**

Returns true if the shape is packed.

**Return type:** bool

**migraphx.transposed()**

Returns true if the shape is transposed.

**Return type:** bool

**migraphx.broadcasted()**

Returns true if the shape is broadcasted.

**Return type:** bool

**migraphx.standard()**

Returns true if the shape is a standard shape. That is, the shape is both packed and not transposed.

**Return type:** bool

**migraphx.scalar()**

Returns true if all strides are equal to 0 (scalar tensor).

**Return type:** bool

## 2.2.2. Argument

**classmigraphx.argument(data)**

Construct an argument from a python buffer. This can include numpy arrays.

**migraphx.get_shape()**

Returns the shape of the argument.

**Return type:** shape

**migraphx.tolist()**

Convert the elements of the argument to a python list.

**Return type:** list

**migraphx.generate_argument(s**, **seed=0)**

Generate an argument with random data.

**Parameters: s** ([*shape*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.shape)) – Shape of argument to generate.

**seed** (*int*) – The seed used for random number generation

**Return type:** [argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)

## 2.2.3. Target

**Class migraphx.target**

This represents the compiliation target.

**migraphx.get_target(name)**

Constructs the target.

**Parameters: name** (*str*) – The name of the target to construct. This can either be ‘gpu’ or ‘ref’.

**Return type:** target

## 2.2.4. Program

**class migraphx.program**

Represents the computation graph to be compiled and run.

**migraphx.clone()**

Make a copy of the program

**Return type:** [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

**migraphx.get_parameter_shapes()**

Get the shapes of all the input parameters in the program.

**Return type:** dict[str, [shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.shape)]

**migraphx.get_shape()**

Get the shape of the final output of the program.

**Return type:** [shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.shape)

**migraphx.compile(t**, **offload_copy=True**, **fast_math=True)**

Compiles the program for the target and optimizes it.

**Parameters**

-   **t** ([*target*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.target)) – This is the target to compile the program for.
-   **offload_copy** (*bool*) – For targets with offloaded memory(such as the gpu), this will insert instructions during compilation to copy the input parameters to the offloaded memory and to copy the final result from the offloaded memory back to main memory.
-   **fast_math** (*bool*) – Optimize math functions to use faster approximate versions. There may be slight accuracy degredation when enabled.

**migraphx.run(params)**

Run the program.

**Parameters: params** (*dict[str,* [*argument*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)*]*) – This is a map of the input parameters which will be used when running the program.

**Returns:** The result of the last instruction.

**Return type:** [argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)

**migraphx.quantize_fp16(prog**, **ins_names=['all'])**

Quantize the program to use fp16.

**Parameters: prog** ([*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)) – Program to quantize.

**ins_names** (*list[str]*) – List of instructions to quantize.

**migraphx.quantize_int8(prog**, **t**, **calibration=[]**, **ins_names=['dot', 'convolution'])**

Quantize the program to use int8.

**Parameters**

-   **prog** ([*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)) – Program to quantize.
-   **t** ([*target*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.target)) – Target that will be used to run the calibration data.
-   **calibration** (*list[dict[str,* [*argument*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)*]]*) – Calibration data used to decide the parameters to the int8 optimization.
-   **ins_names** (*list[str]*) – List of instructions to quantize.

## 2.2.5. parse_onnx

migraphx.parse_onnx(filename, default_dim_value=1, map_input_dims={}, skip_unknown_operators=false, print_program_on_error=false)

Load and parse an onnx file.

**Parameters**

-   **filename** (*str*) – Path to file.
-   **default_dim_value** (*str*) – default batch size to use (if not specified in onnx file).
-   **map_input_dims** (*str*) – Explicitly specify the dims of an input.
-   **skip_unknown_operators** (*str*) – Continue parsing onnx file if an unknown operator is found.
-   **print_program_on_error** (*str*) – Print program if an error occurs.

    **Return type:** [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

## 2.2.6. parse_tf

**migraphx.parse_tf(filename**, **is_nhwc=True**, **batch_size=1)**

Load and parse an tensorflow protobuf file file.

**Parameters**

-   **filename** (*str*) – Path to file.
-   **is_nhwc** (*bool*) – Use nhwc as default format.
-   **batch_size** (*str*) – default batch size to use (if not specified in protobuf).

    **Return type:** [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

## 2.2.7. Load

**migraphx.load(filename**, **format='msgpack')**

Load a MIGraphX program

**Parameters**

-   **filename** (*str*) – Path to file.
-   **format** (*str*) – Format of file. Valid options are msgpack or json.

**Return type:** [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

## 2.2.8. Save

**migraphx.save(p**, **filename**, **format='msgpack')**

Save a MIGraphX program

**Parameters**

-   **p** ([*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)) – Program to save.
-   **filename** (*str*) – Path to file.
-   **format** (*str*) – Format of file. Valid options are msgpack or json.

# 3. C++ User Guide

# 3.1 Defining different modules in detail

## 3.1.1 Shape

**enum migraphx_shape_datatype_t**

An enum to represent the different data type inputs.

*Values:*

**enumerator migraphx_shape_tuple_type**

**enumerator migraphx_shape_bool_type**

**enumerator migraphx_shape_half_type**

**enumerator migraphx_shape_float_type**

**enumerator migraphx_shape_double_type**

**enumerator migraphx_shape_uint8_type**

**enumerator migraphx_shape_int8_type**

**enumerator migraphx_shape_uint16_type**

**enumerator migraphx_shape_int16_type**

**enumerator migraphx_shape_int32_type**

**enumerator migraphx_shape_int64_type**

**enumerator migraphx_shape_uint32_type**

**enumerator migraphx_shape_uint64_type**

# 

**struct migraphx::shape : public migraphx::handle_base\<\>**

Describe shape of tensor.

A shape consists of a data type, lengths of multi-dimension tensor, and strides

**Public Functions**

**inline shape()**

**inline shape(const migraphx_shape \*p)**

**inline shape(migraphx_shape \*p**, **own)**

**inline shape(migraphx_shape \*p**, **borrow)**

**inline shape(**[**migraphx_shape_datatype_t**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv425migraphx_shape_datatype_t) **type)**

Construct a scalar shape.

**inline shape(**[**migraphx_shape_datatype_t**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv425migraphx_shape_datatype_t) **type, std::vector\<size_t\> plengths)**

Construct a shape with its type and lengths. The strides are automatically computed assumming a packed layout.

## 3.1.2 Argument

**struct migraphx::argument : public migraphx::handle_base\<\>**

Arguments to be passed to an migraphx arguments.

An argument represents a raw buffer of data with a shape.

**Public Functions**

**inline argument()**

**inline argument(migraphx_argument \*p**, **borrow)**

**inline argument(migraphx_argument \*p**, **own)**

**inline argument(const migraphx_argument \*p)**

**inline argument(**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) **pshape, void \*pbuffer)**

**inline** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) **get_shape() const**

**inline char \*data() const**

Public Static Functions

**static inline** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) **generate(**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) **ps, size_t pseed = 0)**

Generate an argument using random data.

**Friends**

**inline** **friend** **friend** **bool** **operator==** **(const** **argument** **\&px,** **const** **argument** **\&py)**

**inline** **friend** **friend** **bool** **operator!=** **(const** **argument** **\&px,** **const** **argument** **\&py)**

## 3.1.3 Target

**struct migraphx::target : public migraphx::handle_base\<\>**

A

target for compilation.

**Public Functions**

**inline target()**

**inline target(migraphx_target \*p**, **own)**

**inline target(migraphx_target \*p**, **borrow)**

**inline target(const char \*name)**

Construct a target from its name.

## 3.1.4 Program

**struct migraphx::program_parameter_shapes : public migraphx::handle_base\<\>**

Public Functions

**inline program_parameter_shapes()**

**inline program_parameter_shapes(migraphx_program_parameter_shapes \*p**, **own)**

**inline program_parameter_shapes(migraphx_program_parameter_shapes \*p**, **borrow)**

**inline size_t size() const**

**inline** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) **operator[](const char \*pname) const**

**inline std::vector\<const char\*\> names() const**

**struct migraphx::program_parameters : public migraphx::handle_base\<\>**

A class to construct the inputs parameters for a program.

**Public Functions**

**inline program_parameters(migraphx_program_parameters \*p**, **own)**

**inline program_parameters(migraphx_program_parameters \*p**, **borrow)**

**inline program_parameters(migraphx_program_parameters \*p)**

**inline program_parameters()inline program_parameters(std::initializer_list\<std::pair\<std::string,** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE)**\>\> l)**

Construct the parameters from initializer_list.

**inline void add(const char \*pname, const** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) **\&pargument) const**

Add a new parameter.

**struct migraphx_compile_options**

**Public Functions**

**template\<class ...Ts\>  
inline migraphx_compile_options(**[**Ts**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4IDpEN24migraphx_compile_options24migraphx_compile_optionsEDpRR2Ts)**&&... xs)**

**Public Members**

**migraphx::compile_options object**

**struct migraphx::program : public migraphx::handle_base\<\>**

A program represents the all computation graphs to be compiled and executed.

**Public Functions**

**inline program()**

**inline program(migraphx_program \*p**, **own)**

**inline program(migraphx_program \*p**, **borrow)**

**inline void compile(const** [**target**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx6targetE) **\&ptarget, const compile_options \&poptions) const**

Compile the program for a specific target to be ran on.

**inline void compile(const** [**target**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx6targetE) **\&ptarget) const**

Compile the program for a specific target to be ran on.

**inline** [**program_parameter_shapes**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx24program_parameter_shapesE) **get_parameter_shapes() const**

Return the shapes for the input parameters.

**inline shapes get_output_shapes() const**

Get the shapes of all the outputs returned by this program.

**inline arguments eval(const** [**program_parameters**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx18program_parametersE) **\&pparams) const**

Run the program using the inputs passed in.

**inline void print() const**

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **sort()**

**inline module get_main_module()**

**Friends**

**inline** **friend** **friend** **bool** **operator==** **(const** **program** **\&px,** **const** **program** **\&py)**

**inline** **friend** **friend** **bool** **operator!=** **(const** **program** **\&px,** **const** **program** **\&py)**

## 3.1.5 Quantize

**struct migraphx::quantize_op_names : public migraphx::handle_base\<\>**

**Public Functions**

**inline quantize_op_names()**

**inline quantize_op_names(migraphx_quantize_op_names \*p**, **own)**

**inline void add(const std::string \&name)**

**inline void migraphx::quantize_fp16(const** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **\&prog)**

Quantize program to use fp16.

**inline void migraphx::quantize_fp16(const** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **\&prog, const** [**quantize_op_names**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx17quantize_op_namesE) **\&names)**

Quantize program to use fp16.

**struct migraphx::quantize_int8_options : public migraphx::handle_base\<\>**

Options to be passed when quantizing for int8.

**Public Functions**

**inline quantize_int8_options()**

**inline quantize_int8_options(migraphx_quantize_int8_options \*p**, **own)**

**inline quantize_int8_options(migraphx_quantize_int8_options \*p**, **borrow)**

**inline void add_op_name(const std::string \&name)**

Add an operator that should be quantized.

**inline void add_calibration_data(const** [**program_parameters**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx18program_parametersE) **\&pp)**

Add calibrartion data to be used for quantizing.

**Public Members**

**std::vector\<parameter_map\> calibration = {}**

**std::vector\<std::string\> op_names = {}**

**inline void migraphx::quantize_int8(const** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **\&prog, const** [**target**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx6targetE) **\&ptarget, const** [**quantize_int8_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx21quantize_int8_optionsE) **\&options)**

Quantize program to use int8.

## 3.1.6 parse_onnx

**struct migraphx::onnx_options : public migraphx::handle_base\<\>**

Options for parsing onnx options.

**Public Functions**

**inline onnx_options()**

**inline onnx_options(migraphx_onnx_options \*p**, **own)**

**inline void set_input_parameter_shape(const std::string \&name**, **std::vector\<std::size_t\> dim)**

Make onnx parser treat an inputs with a certain dimensions.

**inline void set_default_dim_value(unsigned int value)**

When there is a dimension parameter, then use this default value.

**inline void set_default_loop_iterations(int64_t value)**

Set default max iteration number for the loop operator.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx(const char \*filename)**

Parse an onnx file into a migraphx program.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx(const char \*filename, const migraphx::**[**onnx_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx12onnx_optionsE) **\&options)**

Parse an onnx file into a migraphx program.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const std::string \&buffer)**

Parse a buffer of memory as an onnx file.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const std::string \&buffer, const migraphx::**[**onnx_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx12onnx_optionsE) **\&options)**

Parse a buffer of memory as an onnx file.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const void \*data, size_t size)**

Parse a buffer of memory as an onnx file.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const void \*data, size_t size, const migraphx::**[**onnx_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx12onnx_optionsE) **\&options)**

Parse a buffer of memory as an onnx file.

## 3.1.7 Load

**struct migraphx_file_options**

**Public Functions**

**template\<class ...Ts\>  
inline migraphx_file_options(**[**Ts**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4IDpEN21migraphx_file_options21migraphx_file_optionsEDpRR2Ts)**&&... xs)**

**Public Members**

**migraphx::file_options object**

Load a saved migraphx program from a file.

## 3.1.8 Save

**inline void migraphx::save(const** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **\&p, const char \*filename)**

Save a program to a file.

# 4. MIGraphX Driver

# 4.1 Description

The MIGraphX driver is a tool that allows you to utilize many of the core functions of MIGraphX without having to write your own program.

# 4.2 How to Use

The MIGraphX driver is installed with MIGraphX and can be found in */opt/rocm/bin/migraphx-driver*, or in *AMDMIGraphX/build/bin/migraphx-driver* after building the source code.

See below for a comprehensive list of commands and option arguments, as well as some usage examples.

## 4.2.1 Commands

## 

![Graphical user interface, text, application, email Description automatically generated](media/19520c77695364dfd7eed063ccad316c.png)

## 4.2.2 Options

## 

## ![Graphical user interface, application, email Description automatically generated](media/55968d31b828db50711928931e75d299.png)

# 

# 4.3 Defining different modules in detail

## 4.3.1 Read

Loads and prints input graph.

**\<input file\>**

File to load

**--model [resnet50\|inceptionv3\|alexnet]**

Load model

\--onnx

Load as onnx

\--tf

Load as tensorflow

\--migraphx

Load as MIGraphX

\--migraphx-json

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1)

Set batch size for model

\--nhwc

Treat tensorflow format as nhwc

\--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

\--nchw

Treat tensorflow format as nchw

\--trim, -t [unsigned int]

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>]

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O

Optimize when reading

\--graphviz, -g

Print out a graphviz representation.

\--brief

Make the output brief.

\--cpp

Print out the program as cpp program.

\--json

Print out program as json.

\--text

Print out program in text format.

\--binary

Print out program in binary format.

\--output, -o [std::string]

Output to file.

## 4.3.2 compile

Compiles and prints input graph.

\<input file\>

File to load

\--model [resnet50\|inceptionv3\|alexnet]

Load model

\--onnx

Load as onnx

\--tf

Load as tensorflow

\--migraphx

Load as MIGraphX

\--migraphx-json

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1)

Set batch size for model

\--nhwc

Treat tensorflow format as nhwc

\--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

\--nchw

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-int8>

Quantize for int8

## 4.3.3 Run <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#run>

Loads and prints input graph.

\<input file\> <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-arg-input>

File to load

\--model [resnet50\|inceptionv3\|alexnet] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-model>

Load model

\--onnx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-onnx>

Load as onnx

\--tf <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-tf>

Load as tensorflow

\--migraphx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-migraphx>

Load as MIGraphX

\--migraphx-json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-migraphx-json>

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-batch>

Set batch size for model

\--nhwc <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-nhwc>

Treat tensorflow format as nhwc

\--skip-unknown-operators <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-skip-unknown-operators>

Skip unknown operators when parsing and continue to parse.

\--nchw <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-nchw>

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-int8>

Quantize for int8

## 4.3.4 Perf <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#perf>

Compiles and runs input graph then prints performance report.

\<input file\> <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-arg-input>

File to load

\--model [resnet50\|inceptionv3\|alexnet] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-model>

Load model

\--onnx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-onnx>

Load as onnx

\--tf <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-tf>

Load as tensorflow

\--migraphx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-migraphx>

Load as MIGraphX

\--migraphx-json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-migraphx-json>

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-batch>

Set batch size for model

\--nhwc <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-nhwc>

Treat tensorflow format as nhwc

\--skip-unknown-operators <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-skip-unknown-operators>

Skip unknown operators when parsing and continue to parse.

\--nchw <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-nchw>

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-int8>

Quantize for int8

\--iterations, -n [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-iterations>

Number of iterations to run for perf report (Default: 100)

## 4.3.5 Verify <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#verify>

Runs reference and CPU or GPU implementations and checks outputs for consistency.

\<input file\> <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-arg-input>

File to load

\--model [resnet50\|inceptionv3\|alexnet] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-model>

Load model

\--onnx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-onnx>

Load as onnx

\--tf <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-tf>

Load as tensorflow

\--migraphx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-migraphx>

Load as MIGraphX

\--migraphx-json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-migraphx-json>

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-batch>

Set batch size for model

\--nhwc <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-nhwc>

Treat tensorflow format as nhwc

\--skip-unknown-operators <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-skip-unknown-operators>

Skip unknown operators when parsing and continue to parse.

\--nchw <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-nchw>

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-int8>

Quantize for int8

\--tolerance [double] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-tolerance>

Tolerance for errors (Default: 80)

\-i, --per-instruction <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-i>

Verify each instruction

\-r, --reduce <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-r>

Reduce program and verify

## 4.3.6 Roctx

Provides marker information for each operation, allowing MIGraphX to be used with [rocprof](https://rocmdocs.amd.com/en/latest/ROCm_Tools/ROCm-Tools.html) for performance analysis. This allows user to get GPU-level kernel timing information. An example command line combined with rocprof for tracing purposes is given below:

/opt/rocm/bin/rocprof --hip-trace --roctx-trace --flush-rate 1ms --timestamp on -d \<OUTPUT_PATH\> --obj-tracking on /opt/rocm/bin/migraphx-driver roctx \<ONNX_FILE\> \<MIGRAPHX_OPTIONS\>

After **rocprof** is run, the output directory will contain trace information for HIP, HCC and ROCTX in seperate **.txt** files. To understand the interactions between API calls, it is recommended to utilize **roctx.py** helper script as desribed in dev/tools:rocTX section.

\<input file\> <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-arg-input>

File to load

\--model [resnet50\|inceptionv3\|alexnet] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-model>

Load model

\--onnx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-onnx>

Load as onnx

\--tf <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-tf>

Load as tensorflow

\--migraphx <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-migraphx>

Load as MIGraphX

\--migraphx-json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-migraphx-json>

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-batch>

Set batch size for model

\--nhwc <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-nhwc>

Treat tensorflow format as nhwc

\--skip-unknown-operators <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-skip-unknown-operators>

Skip unknown operators when parsing and continue to parse.

\--nchw <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-nchw>

Treat tensorflow format as nchw

\--trim, -t [unsigned int] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-trim>

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-input-dim>

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-optimize>

Optimize when reading

\--graphviz, -g <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-graphviz>

Print out a graphviz representation.

\--brief <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-brief>

Make the output brief.

\--cpp <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-cpp>

Print out the program as cpp program.

\--json <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-json>

Print out program as json.

\--text <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-text>

Print out program in text format.

\--binary <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-binary>

Print out program in binary format.

\--output, -o [std::string] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-output>

Output to file.

\--fill0 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-fill0>

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-fill1>

Fill parameter with 1s

\--gpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-gpu>

Compile on the gpu

\--cpu <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-cpu>

Compile on the cpu

\--ref <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-ref>

Compile on the reference implementation

\--enable-offload-copy <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-enable-offload-copy>

Enable implicit offload copying

\--disable-fast-math <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-disable-fast-math>

Disable fast math optimization

\--fp16 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-fp16>

Quantize for fp16

\--int8 <https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-int8>

Quantize for int8

# 5. Contributor Guide

# 5.1 MIGraphX Fundamentals

MIGraphX provides an optimized execution engine for deep learning neural networks. We will cover some simple operations in the MIGraphX framework here. For a quick start guide to using MIGraphX, look in the example directory:

https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/tree/develop/examples/migraphx.

## 5.1.1 Location of the Examples

The ref_dev_examples.cpp can be found in the test directory (/test). The executable file test_ref_dev_examples based on this file will be created in the bin/ of the build directory after running make -j\$(nproc) test_ref_dev_examples. The executable will also be created when running make -j\$(nproc) check, alongside with all the other tests. Directions for building MIGraphX from source can be found in the main README file:

[https://github.com/ROCmSoftwarePlatform/AMDMIGraphX\#readme](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#readme).

## 5.1.2 Adding Two Literals

A program is a collection of modules, which are collections of instructions to be executed when calling [**eval**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4NK8migraphx7program4evalERK18program_parameters). Each instruction has an associated **operation** which represents the computation to be performed by the instruction.

We start with a snippet of the simple add_two_literals() function:

*// create the program and get a pointer to the main module*

migraphx::program p;

**auto**\* mm = p.get_main_module();

*// add two literals to the program*

**auto** one = mm-\>add_literal(1);

**auto** two = mm-\>add_literal(2);

*// make the add operation between the two literals and add it to the program*

mm-\>add_instruction(migraphx::make_op("add"), one, two);

*// compile the program on the reference device*

p.compile(migraphx::ref::target{});

*// evaulate the program and retreive the result*

**auto** result = p.eval({}).back();

std::cout \<\< "add_two_literals: 1 + 2 = " \<\< result \<\< "**\\n**";

We start by creating a simple migraphx::program object and then getting a pointer to the main module of it. The program is a collection of modules that start executing from the main module, so instructions are added to the modules rather than directly onto the program object. We then use the **add_literal** function to add an instruction that stores the literal number 1 while returning an **instruction_ref**. The returned **instruction_ref** can be used in another instruction as an input. We use the same **add_literal** function to add a 2 to the program. After creating the literals, we then create the instruction to add the numbers together. This is done by using the **add_instruction** function with the "add" **operation** created by **make_op** along with the previous **add_literal** **instruction_ref** for the input arguments of the instruction. Finally, we can run this [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) by compiling it for the reference target (CPU) and then running it with [**eval**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4NK8migraphx7program4evalERK18program_parameters) The result is then retreived and printed to the console.

We can compile the program for the GPU as well, but the file will have to be moved to the test/gpu/ directory and the correct target must be included:

\#include *\<migraphx/gpu/target.hpp\>*

## 

## 5.1.3 Using Parameters

The previous program will always produce the same value of adding 1 and 2. In the next program we want to pass an input to a program and compute a value based on the input. We can modify the program to take an input parameter x, as seen in the add_parameter() function:

migraphx::program p;

**auto**\* mm = p.get_main_module();

migraphx::shape s{migraphx::shape::int32_type, {1}};

*// add a "x" parameter with the shape s*

**auto** x = mm-\>add_parameter("x", s);

**auto** two = mm-\>add_literal(2);

*// add the "add" instruction between the "x" parameter and "two" to the module*

mm-\>add_instruction(migraphx::make_op("add"), x, two);

p.compile(migraphx::ref::target{});

This adds a parameter of type int32, and compiles it for the CPU. To run the program, we need to pass the parameter as a parameter_map when we call [**eval**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4NK8migraphx7program4evalERK18program_parameters). We create the parameter_map by setting the x key to an [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) object with an int data type:

*// create a parameter_map object for passing a value to the "x" parameter*

std::vector\<int\> data = {4};

migraphx::parameter_map params;

params["x"] = migraphx::argument(s, data.data());

**auto** result = p.eval(params).back();

std::cout \<\< "add_parameters: 4 + 2 = " \<\< result \<\< "**\\n**";

EXPECT(result.at\<int\>() == 6);

## 

## 5.1.4 Handling Tensor Data

In the previous examples we have only been dealing with scalars, but the [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) class can describe multi-dimensional tensors. For example, we can compute a simple convolution:

migraphx::program p;

**auto**\* mm = p.get_main_module();

*// create shape objects for the input tensor and weights*

migraphx::shape input_shape{migraphx::shape::float_type, {2, 3, 4, 4}};

migraphx::shape weights_shape{migraphx::shape::float_type, {3, 3, 3, 3}};

*// create the parameters and add the "convolution" operation to the module*

**auto** input = mm-\>add_parameter("X", input_shape);

**auto** weights = mm-\>add_parameter("W", weights_shape);

mm-\>add_instruction(migraphx::make_op("convolution", {{"padding", {1, 1}}, {"stride", {2, 2}}}), input, weights);

Here we create two parameters for both the input and weights. In the previous examples, we created simple literals, however, most programs will take data from allocated buffers (usually on the GPU). In this case, we can create [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) objects directly from the pointers to the buffers:

*// Compile the program*

p.compile(migraphx::ref::target{});

*// Allocated buffers by the user*

std::vector\<float\> a = ...;

std::vector\<float\> c = ...;

*// Solution vector*

std::vector\<float\> sol = ...;

*// Create the arguments in a parameter_map*

migraphx::parameter_map params;

params["X"] = migraphx::argument(input_shape, a.data());

params["W"] = migraphx::argument(weights_shape, c.data());

*// Evaluate and confirm the result*

**auto** result = p.eval(params).back();

std::vector\<float\> results_vector(64);

result.visit([&](**auto** output) { results_vector.assign(output.begin(), output.end()); });

EXPECT(migraphx::verify_range(results_vector, sol));

An [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) can handle memory buffers from either the GPU or the CPU. By default when running the [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE), buffers are allocated on the corresponding target. When compiling for the CPU, the buffers by default will be allocated on the CPU. When compiling for the GPU, the buffers by default will be allocated on the GPU. With the option offloaf_copy=true set while compiling for the GPU, the buffers will be located on the CPU.

## 5.1.5 Importing From ONNX

A [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) can be built directly from an onnx file using the MIGraphX ONNX parser. This makes it easier to use neural networks directly from other frameworks. In this case, there is an parse_onnx function:

program p = migraphx::parse_onnx("model.onnx");

p.compile(migraphx::gpu::target{});

# 
