***Table Of Contents***

<table 1>
<tr>
<th>Getting Started</th>
<th>Python User Guide</th>
<th>C++ user Guide</th>
<th>MIGraphX Driver</th>
</tr>
<tr>
<td>
<pre>
1. Getting Started Guide for MIGraphX
        1.1. Introduction
		1.1.1. Documentation Roadmap
	1.2. List of prerequisites
	1.3. Installing pre-built packages
	1.4. Building From Source
		1.4.1. Use the ROCm build tool rbuild
		1.4.2. Use cmake to build MIGraphX
		1.4.3. Use docker
 </pre>
</td>
<td>
<pre>
2. Python User Guide
	2.1. Setting path and installing package
	2.2 Defining different modules in detail
		2.2.1. Shape
		2.2.2. Argument
		2.2.3. Target
		2.2.4. Program
		2.2.5. parse_onnx
		2.2.6. parse_tf
		2.2.7. Load
		2.2.8. Save
</pre>
</td>
<td>
<pre>
3. C++ User Guide
	3.1 Defining different modules in detail
		3.1.1 Shape
		3.1.2 Argument
		3.1.3 Target
		3.1.4 Program
		3.1.5 Quantize
		3.1.6 parse_onnx
		3.1.7 Load
</pre>
</td>
<td>
<pre>
4. MIGraphX Driver
	4.1 Description
	4.2 How to Use
		4.2.1 Commands
		4.2.2 Options
	4.3 Defining different modules in detail
		4.3.1 Read	
		4.3.2 compile
		4.3.3 Run
		4.3.4 Perf
		4.3.5 Verify
		4.3.6 Roctx
</pre>
</td>
</table 1>
<table 2>
<tr>
<th>Contributor Guide</th>	
</tr>
<td>
<pre>
5. Contributor Guide
	5.1 MIGraphX Fundamentals
		5.1.1 Location of the Examples
		5.1.2 Adding Two Literals
		5.1.3 Using Parameters
		5.1.4 Handling Tensor Data
		5.1.5 Importing From ONNX
	5.2 Data Types
		5.2.1 Shape
		5.2.2 Literal
		5.2.3 Argument
		5.2.4 raw_data
		5.2.5 Tensor_view
	5.3 Program
		5.3.1 Instruction
		5.3.2 Instruction_ref
		5.3.3 Program
		5.3.4 Parse_onnx
		5.3.5 Parse_tf
		5.3.6 Onnx_options
		5.3.7 Tf_options
	5.4 Targets
		5.4.1 Target
		5.4.2 gpu::target
		5.4.3 cpu::target
	5.5 Passes
		5.5.1 Pass
		5.5.2 Dead_code_elimination
		5.5.3 Eliminate_common_subexpression
		5.5.4 Eliminate_concat
		5.5.5 Eliminate_contiguous
`		5.5.6 Eliminate_identity
		5.5.7 Eliminate_pad
		5.5.8 Propagate_constant
		5.5.9 Rewrite_batchnorm
		5.5.10 Rewrite_rnn
		5.5.11 Schedule
		5.5.12 Simplify_algebra
		5.5.13 Simplify_reshapes
	5.6 Matchers
		5.6.1 Introduction
		5.6.2 Arguments
		5.6.3 Binding
		5.6.4 Finding matches
		5.6.5 Creating matchers
	5.7 Tools
		5.7.1 roctx.py
</td>
</pre>
</table 2>
	[1. Getting Started Guide for MIGraphX](#_Toc101516457)
	[1.1.1. Documentation Roadmap](#_Toc101516459)
	[1.2. List of prerequisites](#_Toc101516460)
	[1.3. Installing pre-built packages](#_Toc101516461)
	[1.4. Building From Source](#_Toc101516462)
	[1.4.2. Use cmake to build MIGraphX](#_Toc101516463)
	[1.4.3. Use docker](#_Toc101516464)

***[2. Python User Guide](#_Toc101516465)***

[2.1. Setting path and installing package](#_Toc101516466)

[2.2 Defining different modules in detail](#_Toc101516467)

[2.2.1. Shape](#_Toc101516468)

[2.2.2. Argument](#_Toc101516469)

[2.2.3. Target](#_Toc101516470)

[2.2.4. Program](#_Toc101516471)

[2.2.5. parse_onnx](#_Toc101516472)

[2.2.6. parse_tf](#_Toc101516473)

[2.2.7. Load](#_Toc101516474)

[2.2.8. Save](#_Toc101516475)

***[3. C++ User Guide](#_Toc101516476)***

[3.1 Defining different modules in detail](#_Toc101516477)

[3.1.1 Shape](#_Toc101516478)

[3.1.2 Argument](#_Toc101516479)

[3.1.3 Target](#_Toc101516480)

[3.1.4 Program](#_Toc101516481)

[3.1.5 Quantize](#_Toc101516482)

[3.1.6 parse_onnx](#_Toc101516483)

[3.1.7 Load](#_Toc101516484)

[3.1.8 Save](#_Toc101516485)

***[4. MIGraphX Driver](#_Toc101516486)***

[4.1 Description](#_Toc101516487)

[4.2 How to Use](#_Toc101516488)

[4.2.1 Commands](#_Toc101516489)

[4.2.2 Options](#_Toc101516490)

[![Graphical user interface, application, email Description automatically generated](media/55968d31b828db50711928931e75d299.png)](#_Toc101516491)

[4.3 Defining different modules in detail](#_Toc101516492)

[4.3.1 Read](#_Toc101516493)

[4.3.2 compile](#_Toc101516494)

[4.3.3 Run](#_Toc101516495)

[4.3.4 Perf](#_Toc101516496)

[4.3.5 Verify](#_Toc101516497)

[4.3.6 Roctx](#_Toc101516498)

[5. Contributor Guide](#_Toc101516499)***

[5.1 MIGraphX Fundamentals](#_Toc101516500)

[5.1.1 Location of the Examples](#_Toc101516501)

[5.1.2 Adding Two Literals](#_Toc101516502)

[5.1.3 Using Parameters](#_Toc101516503)

[5.1.4 Handling Tensor Data](#_Toc101516504)

[5.1.5 Importing From ONNX](#_Toc101516505)

[5.2 Data Types](#_Toc101516506)

[5.2.1 Shape](#_Toc101516507)

[5.2.2 Literal](#_Toc101516508)

[5.2.3 Argument](#_Toc101516509)

[5.2.4 raw_data](#_Toc101516510)

[5.2.5 Tensor_view](#_Toc101516511)

[5.3 Program](#_Toc101516512)

[5.3.1 Instruction](#_Toc101516513)

[5.3.2 Instruction_ref](#_Toc101516514)

[5.3.3 Program](#_Toc101516515)

[5.3.4 Parse_onnx](#_Toc101516516)

[5.3.5 Parse_tf](#_Toc101516517)

[5.3.6 Onnx_options](#_Toc101516518)

[5.3.7 Tf_options](#_Toc101516519)

[5.4 Targets](#_Toc101516520)

[5.4.1 Target](#_Toc101516521)

[5.4.2 gpu::target](#_Toc101516522)

[5.4.3 cpu::target](#_Toc101516523)

[5.5 Passes](#_Toc101516524)

[5.5.1 Pass](#_Toc101516525)

[5.5.2 Dead_code_elimination](#_Toc101516526)

[5.5.3 Eliminate_common_subexpression](#_Toc101516527)

[5.5.4 Eliminate_concat](#_Toc101516528)

[5.5.5 Eliminate_contiguous](#_Toc101516529)

[5.5.6 Eliminate_identity](#_Toc101516530)

[5.5.7 Eliminate_pad](#_Toc101516531)

[5.5.8 Propagate_constant](#_Toc101516532)

[5.5.9 Rewrite_batchnorm](#_Toc101516533)

[5.5.10 Rewrite_rnn](#_Toc101516534)

[5.5.11 Schedule](#_Toc101516535)

[5.5.12 Simplify_algebra](#_Toc101516536)

[5.5.13 Simplify_reshapes](#_Toc101516537)

[5.6 Matchers](#_Toc101516538)

[5.6.1 Introduction](#_Toc101516539)

[5.6.2 Arguments](#_Toc101516540)

[5.6.3 Binding](#_Toc101516541)

[5.6.4 Finding matches](#_Toc101516542)

[5.6.5 Creating matchers](#_Toc101516543)

[5.7 Tools](#_Toc101516544)

[5.7.1 roctx.py](#_Toc101516545)

# 

# 1. Getting Started Guide for MIGraphX

# 1.1. Introduction

The MIGraphX execution provider uses AMD's Deep Learning graph optimization engine to accelerate ONNX model on AMD GPUs.

ONNX Runtime is an accelerator for machine learning models with multi platform support and a flexible interface to integrate with hardware-specific libraries. ONNX Runtime can be used with models from PyTorch, Tensorflow/Keras, TFLite, scikit-learn, and other frameworks.

The document also contains an Python User guide, C++ user Guide, MIGraphX Driver and Contributor Guide.

## 1.1.1. Documentation Roadmap

The following is a list of MIGraphX documents in the suggested reading order:

-   Getting Started Guide (this document): In this section we have introduce MIGraphX, ONNX Runtime.
-   Python User Guide: In this section we will be defining different modules like shape, target, argument, save, load, etc.
-   C++ Reference: Describe modules like shape, argument, load, parse_onnx, etc.
-   MIGraphX Driver: Under this section we will cover modules like perf, verify, roctx, etc.
-   Contributor’s Guide: Provides detailed information about MIGraphX Fundamentals, datatypes, operators, targets, etc.

# 1.2. List of prerequisites

The following is a list of prerequisites required to build MIGraphX source.

-   [ROCm cmake modules](https://github.com/RadeonOpenCompute/rocm-cmake) required
-   [MIOpen](https://github.com/ROCmSoftwarePlatform/MIOpen) for running on the GPU
-   [rocBLAS](https://github.com/ROCmSoftwarePlatform/rocBLAS) for running on the GPU
-   [HIP](https://github.com/ROCm-Developer-Tools/HIP) for running on the GPU
-   [Protobuf](https://github.com/google/protobuf) for reading onnx files
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

    This approach uses rbuild to install the prerequisites and build the libs with just one command.

-   [Use cmake](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-cmake-to-build-migraphx)

    This approach uses a script to install the prerequisites, then use cmake to build the source.

-   [Use docker](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-docker)

    This approach builds a docker image with all prerequisites installed, then build the MIGraphX sources inside a docker container.

#### **1.4.1. Use the ROCm build tool rbuild**.

In this approach, we use the rbuild build tool to build MIGraphX. The specific steps are as follows:

1.  Install rocm-cmake, pip3, rocblas, and miopen-hip with the command

sudo apt update && sudo apt install -y rocm-cmake python3-pip rocblas miopen-hip

1.  Install rbuild (sudo may be required here.)

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

**inline shape(migraphx_shape_datatype_t type)**

Construct a scalar shape.

**inline shape(migraphx_shape_datatype_t** **type, std::vector\<size_t\> plengths)**

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

**inline program_parameter_shapes get_parameter_shapes() const**

Return the shapes for the input parameters.

**inline shapes get_output_shapes() const**

Get the shapes of all the outputs returned by this program.

**inline arguments eval(const program_parameters \&pparams) const**

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

**inline void add_calibration_data(const program_parameters \&pp)**

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

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx(const char \*filename, const migraphx::onnx_options** **\&options)**

Parse an onnx file into a migraphx program.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const std::string \&buffer)**

Parse a buffer of memory as an onnx file.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const std::string \&buffer, const migraphx::onnx_options** **\&options)**

Parse a buffer of memory as an onnx file.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const void \*data, size_t size)**

Parse a buffer of memory as an onnx file.

**inline** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) **migraphx::parse_onnx_buffer(const void \*data, size_t size, const migraphx::onnx_options** **\&options)**

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

\--trim, -t [unsigned int] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-trim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-trim)

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-input-dim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-input-dim)

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-optimize](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-optimize)

Optimize when reading

\--graphviz, -g [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-graphviz](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-graphviz)

Print out a graphviz representation.

\--brief [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-brief](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-brief)

Make the output brief.

\--cpp

Print out the program as cpp program.

\--json

Print out program as json.

\--text [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-text](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-text)

Print out program in text format.

\--binary [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-binary](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-binary)

Print out program in binary format.

\--output, -o [std::string] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-output](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-output)

Output to file.

\--fill0 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-fill0](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-fill0)

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-fill1](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-fill1)

Fill parameter with 1s

\--gpu

Compile on the gpu

\--cpu

Compile on the cpu

\--ref [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-ref)

Compile on the reference implementation

\--enable-offload-copy [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-enable-offload-copy](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-enable-offload-copy)

Enable implicit offload copying

\--disable-fast-math [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-disable-fast-math](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-disable-fast-math)

Disable fast math optimization

\--fp16 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-fp16](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-fp16)

Quantize for fp16

\--int8 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-compile-int8](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-compile-int8)

Quantize for int8

## 4.3.3 Run

Loads and prints input graph.

\<input file\> [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-arg-input](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-arg-input)

File to load

\--model [resnet50\|inceptionv3\|alexnet] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-model](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-model)

Load model

\--onnx

Load as onnx

\--tf

Load as tensorflow

\--migraphx

Load as MIGraphX

\--migraphx-json

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-batch](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-batch)

Set batch size for model

\--nhwc

Treat tensorflow format as nhwc

\--skip-unknown-operators [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-skip-unknown-operators](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-skip-unknown-operators)

Skip unknown operators when parsing and continue to parse.

\--nchw

Treat tensorflow format as nchw

\--trim, -t [unsigned int] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-trim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-trim)

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-input-dim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-input-dim)

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-optimize](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-optimize)

Optimize when reading

\--graphviz, -g [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-graphviz](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-graphviz)

Print out a graphviz representation.

\--brief [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-brief](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-brief)

Make the output brief.

\--cpp

Print out the program as cpp program.

\--json

Print out program as json.

\--text [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-text](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-text)

Print out program in text format.

\--binary [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-binary](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-binary)

Print out program in binary format.

\--output, -o [std::string] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-output](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-output)

Output to file.

\--fill0 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-fill0](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-fill0)

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-fill1](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-fill1)

Fill parameter with 1s

\--gpu

Compile on the gpu

\--cpu

Compile on the cpu

\--ref [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-ref)

Compile on the reference implementation

\--enable-offload-copy [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-enable-offload-copy](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-enable-offload-copy)

Enable implicit offload copying

\--disable-fast-math [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-disable-fast-math](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-disable-fast-math)

Disable fast math optimization

\--fp16 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-fp16](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-fp16)

Quantize for fp16

\--int8 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-run-int8](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-run-int8)

Quantize for int8

## 4.3.4 Perf

Compiles and runs input graph then prints performance report.

\<input file\> [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-arg-input](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-arg-input)

File to load

\--model [resnet50\|inceptionv3\|alexnet] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-model](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-model)

Load model

\--onnx

Load as onnx

\--tf

Load as tensorflow

\--migraphx

Load as MIGraphX

\--migraphx-json

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-batch](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-batch)

Set batch size for model

\--nhwc

Treat tensorflow format as nhwc

\--skip-unknown-operators [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-skip-unknown-operators](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-skip-unknown-operators)

Skip unknown operators when parsing and continue to parse.

\--nchw

Treat tensorflow format as nchw

\--trim, -t [unsigned int] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-trim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-trim)

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-input-dim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-input-dim)

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-optimize](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-optimize)

Optimize when reading

\--graphviz, -g [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-graphviz](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-graphviz)

Print out a graphviz representation.

\--brief [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-brief](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-brief)

Make the output brief.

\--cpp

Print out the program as cpp program.

\--json

Print out program as json.

\--text [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-text](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-text)

Print out program in text format.

\--binary [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-binary](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-binary)

Print out program in binary format.

\--output, -o [std::string] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-output](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-output)

Output to file.

\--fill0 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-fill0](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-fill0)

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-fill1](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-fill1)

Fill parameter with 1s

\--gpu

Compile on the gpu

\--cpu

Compile on the cpu

\--ref [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-ref)

Compile on the reference implementation

\--enable-offload-copy [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-enable-offload-copy](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-enable-offload-copy)

Enable implicit offload copying

\--disable-fast-math [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-disable-fast-math](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-disable-fast-math)

Disable fast math optimization

\--fp16 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-fp16](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-fp16)

Quantize for fp16

\--int8 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-int8](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-int8)

Quantize for int8

\--iterations, -n [unsigned int] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-perf-iterations](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-perf-iterations)

Number of iterations to run for perf report (Default: 100)

## 4.3.5 Verify

Runs reference and CPU or GPU implementations and checks outputs for consistency.

\<input file\> [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-arg-input](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-arg-input)

File to load

\--model [resnet50\|inceptionv3\|alexnet] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-model](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-model)

Load model

\--onnx

Load as onnx

\--tf

Load as tensorflow

\--migraphx

Load as MIGraphX

\--migraphx-json

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-batch](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-batch)

Set batch size for model

\--nhwc

Treat tensorflow format as nhwc

\--skip-unknown-operators [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-skip-unknown-operators](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-skip-unknown-operators)

Skip unknown operators when parsing and continue to parse.

\--nchw

Treat tensorflow format as nchw

\--trim, -t [unsigned int] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-trim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-trim)

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-input-dim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-input-dim)

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-optimize](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-optimize)

Optimize when reading

\--graphviz, -g [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-graphviz](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-graphviz)

Print out a graphviz representation.

\--brief [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-brief](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-brief)

Make the output brief.

\--cpp

Print out the program as cpp program.

\--json

Print out program as json.

\--text [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-text](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-text)

Print out program in text format.

\--binary [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-binary](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-binary)

Print out program in binary format.

\--output, -o [std::string] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-output](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-output)

Output to file.

\--fill0 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-fill0](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-fill0)

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-fill1](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-fill1)

Fill parameter with 1s

\--gpu

Compile on the gpu

\--cpu

Compile on the cpu

\--ref [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-ref)

Compile on the reference implementation

\--enable-offload-copy [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-enable-offload-copy](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-enable-offload-copy)

Enable implicit offload copying

\--disable-fast-math [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-disable-fast-math](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-disable-fast-math)

Disable fast math optimization

\--fp16 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-fp16](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-fp16)

Quantize for fp16

\--int8 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-int8](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-int8)

Quantize for int8

\--tolerance [double] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-tolerance](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-tolerance)

Tolerance for errors (Default: 80)

\-i, --per-instruction [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-i](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-i)

Verify each instruction

\-r, --reduce [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-verify-r](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-verify-r)

Reduce program and verify

## 4.3.6 Roctx

Provides marker information for each operation, allowing MIGraphX to be used with rocprof for performance analysis. This allows user to get GPU-level kernel timing information. An example command line combined with rocprof for tracing purposes is given below:

/opt/rocm/bin/rocprof --hip-trace --roctx-trace --flush-rate 1ms --timestamp on -d \<OUTPUT_PATH\> --obj-tracking on /opt/rocm/bin/migraphx-driver roctx \<ONNX_FILE\> \<MIGRAPHX_OPTIONS\>

After **rocprof** is run, the output directory will contain trace information for HIP, HCC and ROCTX in seperate **.txt** files. To understand the interactions between API calls, it is recommended to utilize **roctx.py** helper script as desribed in dev/tools:rocTX section.

\<input file\> [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-arg-input](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-arg-input)

File to load

\--model [resnet50\|inceptionv3\|alexnet] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-model](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-model)

Load model

\--onnx

Load as onnx

\--tf

Load as tensorflow

\--migraphx

Load as MIGraphX

\--migraphx-json

Load as MIGraphX JSON

\--batch [unsigned int] (Default: 1) [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-batch](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-batch)

Set batch size for model

\--nhwc

Treat tensorflow format as nhwc

\--skip-unknown-operators [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-skip-unknown-operators](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-skip-unknown-operators)

Skip unknown operators when parsing and continue to parse.

\--nchw

Treat tensorflow format as nchw

\--trim, -t [unsigned int] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-trim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-trim)

Trim instructions from the end (Default: 0)

\--input-dim [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-input-dim](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-input-dim)

Dim of a parameter (format: “@name d1 d2 dn”)

\--optimize, -O [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-optimize](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-optimize)

Optimize when reading

\--graphviz, -g [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-graphviz](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-graphviz)

Print out a graphviz representation.

\--brief [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-brief](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-brief)

Make the output brief.

\--cpp

Print out the program as cpp program.

\--json

Print out program as json.

\--text [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-text](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-text)

Print out program in text format.

\--binary [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-binary](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-binary)

Print out program in binary format.

\--output, -o [std::string] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-output](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-output)

Output to file.

\--fill0 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-fill0](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-fill0)

Fill parameter with 0s

\--fill1 [std::vector\<std::string\>] [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-fill1](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-fill1)

Fill parameter with 1s

\--gpu

Compile on the gpu

\--cpu

Compile on the cpu

\--ref [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-ref)

Compile on the reference implementation

\--enable-offload-copy [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-enable-offload-copy](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-enable-offload-copy)

Enable implicit offload copying

\--disable-fast-math [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-disable-fast-math](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-disable-fast-math)

Disable fast math optimization

\--fp16 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-fp16](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-fp16)

Quantize for fp16

\--int8 [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html\#cmdoption-migraphx-driver-roctx-int8](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/driver.html#cmdoption-migraphx-driver-roctx-int8)

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

# 5.2 Data Types

## 5.2.1 Shape

**struct migraphx::internal::shape**

**Public Types**

**enum type_t**

*Values:*

**enumerator bool_typet**

**enumerator half_type**

**enumerator float_type**

**enumerator double_type**

**enumerator uint8_type**

**enumerator int8_type**

**enumerator uint16_type**

**enumerator int16_type**

**enumerator int32_type**

**enumerator int64_type**

**enumerator uint32_type**

**enumerator uint64_type**

**enumerator tuple_type**

**Public Functions**

**shape()**

**shape(type_t t)**

**shape(type_t t, std::vector\<std::size_t\> l)**

**shape(type_t** **t, std::vector\<std::size_t\> l, std::vector\<std::size_t\> s)**

**template\<class Range\>  
inline shape(type_t t, const** [**Range**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape5shapeE6type_tRK5Range) **\&l)**

**template\<class Range1, class Range2\>  
inline shape(type_t t, const** [**Range1**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I00EN8migraphx8internal5shape5shapeE6type_tRK6Range1RK6Range2) **\&l, const** [**Range2**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I00EN8migraphx8internal5shape5shapeE6type_tRK6Range1RK6Range2) **\&s)**

**shape(const std::vector\<**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape5shapeERKNSt6vectorI5shapeEE)**\> \&subs)**

[**type_t**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_tE) **type() const**

**const std::vector\<std::size_t\> \&lens() const**

**const std::vector\<std::size_t\> \&strides() const**

**std::size_t elements() const**

**std::size_t bytes() const**

**std::size_t type_size() const**

**std::size_t index(std::initializer_list\<std::size_t\> l) const**

Map multiple indices to space index.

**std::size_t index(const std::vector\<std::size_t\> \&l) const**

Map multiple indices to space index.

**template\<class Iterator\>  
inline std::size_t index(**[**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal5shape5indexENSt6size_tE8Iterator8Iterator) **start,** [**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal5shape5indexENSt6size_tE8Iterator8Iterator) **last) const**

Map multiple indices from a range of iterator to a space index.

**std::size_t index(std::size_t i) const**

Map element index to space index.

**std::vector\<std::size_t\> multi(std::size_t i) const**

**void multi_copy(std::size_t i, std::size_t \*start, const std::size_t \*end) const**

**bool packed() const**

Returns true if the shape is packed with no padding.

**bool transposed() const**

Returns true is the shape has been transposed. That is the strides are not in descending order

**bool broadcasted() const**

Returns true if the shape is broadcasting a dimension. That is, one of the strides are zero.

**bool standard() const**

Returns true if the shape is in its standard format. That is, the shape is both packed and not transposed.

**bool scalar() const**

Returns true if all strides are equal to 0 (scalar tensor)

[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **normalize_standard() const**

[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **with_lens(type_t** **t, const std::vector\<std::size_t\> \&l) const**

[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **with_lens(const std::vector\<std::size_t\> \&l) const**

**template\<class ...Visitors\>  
inline void visit_type(**[**Visitors**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4IDpENK8migraphx8internal5shape10visit_typeEvDp8Visitors)**... vs) const**

**std::string type_string() const**

**const std::vector\<**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE)**\> \&sub_shapes() const**

**Public Static Functions**

**static const std::vector\<type_t\> \&types()**

**static std::string name(type_t t)**

**static std::string cpp_type(type_t t)**

**static** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **from_permutation(type_t** **t, const std::vector\<std::size_t\> \&l, const std::vector\<int64_t\> \&perm**

**template\<class Visitor, class TupleVisitor\>  
static inline void visit(type_t t,** [**Visitor**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I00EN8migraphx8internal5shape5visitEv6type_t7Visitor12TupleVisitor) **v, TupleVisitor tv)**

**template\<class Visitor\>  
static inline void visit(type_t t,** [**Visitor**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape5visitEv6type_t7Visitor) **v)**

**template\<class Visitor\>  
static inline void visit_types(**[**Visitor**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape11visit_typesEv7Visitor) **v)**

**static type_t parse_type(const std::string \&s)**

**Friends**

**friend** **friend** **bool** **operator==** **(const** **shape** **\&x,** **const** **shape** **\&y)**

**friend friend bool operator!= (const shape \&x, const shape \&y)**

**friend friend std::ostream & operator\<\< (std::ostream \&os, const shape \&x)**

**template\<class T\>  
struct as**

**Public Types**

**using type = std::conditional_t\<std::is_same\<**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape2asE)**, bool\>{}, int8_t,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape2asE)**\>**

**Public Functions**

**inline** [**type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape2as4typeE) **max() const**

**inline** [**type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape2as4typeE) **min() const**

**template\<class U\>  
inline** [**type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape2as4typeE) **operator()(**[**U**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal5shape2asclE4type1U) **u) const**

**template\<class U\>  
inline** [**type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape2as4typeE) **\*operator()(**[**U**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal5shape2asclEP4typeP1U) **\*u) const**

**template\<class U\>  
inline const** [**type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape2as4typeE) **\*operator()(const** [**U**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal5shape2asclEPK4typePK1U) **\*u) const**

**inline** [**type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape2as4typeE) **operator()() const**

**inline std::size_t size(std::size_t n = 1) const**

**template\<class U\>  
inline** [**type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape2as4typeE) **\*from(**[**U**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal5shape2as4fromEP4typeP1UNSt6size_tE) **\*buffer, std::size_t n = 0) const**

**template\<class U\>  
inline const** [**type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape2as4typeE) **\*from(const** [**U**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal5shape2as4fromEPK4typePK1UNSt6size_tE) **\*buffer, std::size_t n = 0) const**

**inline type_t type_enum() const**

**template\<class T, class = void\>**  
**struct get_type**

**template\<class T\>  
struct get_type\<bool,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeIb1TEE)**\> : public std::integral_constant\<type_t,** [**bool_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t9bool_typeE)**\>**

**template\<class T\>  
struct get_type\<const** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeIK1TEE)**\> : public migraphx::internal::**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE)**::get_type\<**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeIK1TEE)**\>**

**template\<class T\>  
struct get_type\<double,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeId1TEE)**\> : public std::integral_constant\<type_t,** [**double_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t11double_typeE)**\>**

**template\<class T\>  
struct get_type\<float,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeIf1TEE)**\> : public std::integral_constant\<type_t,** [**float_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t10float_typeE)**\>**` `**template\<class T\>  
struct get_type\<half,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeI4half1TEE)**\> : public std::integral_constant\<type_t,** [**half_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t9half_typeE)**\>**

**template\<class T\>  
struct get_type\<int16_t,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeI7int16_t1TEE)**\> : public std::integral_constant\<type_t,** [**int16_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t10int16_typeE)**\>**

**template\<class T\>  
struct get_type\<int32_t,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeI7int32_t1TEE)**\> : public std::integral_constant\<type_t,** [**int32_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t10int32_typeE)**\>**

**template\<class T\>  
struct get_type\<int64_t,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeI7int64_t1TEE)**\> : public std::integral_constant\<type_t,** [**int64_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t10int64_typeE)**\>**

**template\<class T\>  
struct get_type\<int8_t,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeI6int8_t1TEE)**\> : public std::integral_constant\<type_t,** [**int8_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t9int8_typeE)**\>**

**template\<class T\>  
struct get_type\<uint16_t,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeI8uint16_t1TEE)**\> : public std::integral_constant\<type_t,** [**uint16_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t11uint16_typeE)**\>**

**template\<class T\>  
struct get_type\<uint32_t,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeI8uint32_t1TEE)**\> : public std::integral_constant\<type_t,** [**uint32_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t11uint32_typeE)**\>**

**template\<class T\>  
struct get_type\<uint64_t,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeI8uint64_t1TEE)**\> : public std::integral_constant\<type_t,** [**uint64_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t11uint64_typeE)**\>**

**template\<class T\>  
struct get_type\<uint8_t,** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal5shape8get_typeI7uint8_t1TEE)**\> : public std::integral_constant\<type_t,** [**uint8_type**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shape6type_t10uint8_typeE)**\>**

## 5.2.2 Literal

**struct migraphx::internal::literal : public migraphx::internal::raw_data\<**[**literal**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal7literalE)**\>**

Represents a raw literal.

This stores the literal has a raw buffer that is owned by this class

**Public Functions**

**inline literal()**

**template\<class U, class T = deduce\<**[**U**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I00_N5shape6type_tEEN8migraphx8internal7literal7literalE1U)**\>,** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE)**::type_t** **ShapeType =** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE)**::get_type\<**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I00_N5shape6type_tEEN8migraphx8internal7literal7literalE1U)**\>{}\>**  
**inline literal(**[**U**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I00_N5shape6type_tEEN8migraphx8internal7literal7literalE1U) **x)**

**template\<class T\>**  
**inline literal(const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&s**, **const std::vector\<**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal7literal7literalERK5shapeRKNSt6vectorI1TEE)**\> \&x)**

**template\<class T\>**  
**inline literal(const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&s**, **const std::initializer_list\<**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal7literal7literalERK5shapeRKNSt16initializer_listI1TEE)**\> \&x)**

**template\<class Iterator\>**  
**inline literal(const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&s**, [**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal7literal7literalERK5shape8Iterator8Iterator) **start**, [**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal7literal7literalERK5shape8Iterator8Iterator) **end)**

**template\<class T, long PrivateRequires__LINE_\_ = \_LINE_, typename std::enable_if\<(PrivateRequires__LINE_\_** **== \_LINE\_ && (migraphx::and_\<sizeof(**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXeqst1TL1EEEEEEiE4typeEEN8migraphx8internal7literal7literalERK5shapeP1T)**) == 1\>{})), int\>::type = 0\>**  
**inline literal(const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&s**, [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXeqst1TL1EEEEEEiE4typeEEN8migraphx8internal7literal7literalERK5shapeP1T) **\*x)**

**inline bool empty() const**

Whether data is available.

**inline const char \*data() const**

Provides a raw pointer to the data.

**inline const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&get_shape() const**

**inline std::vector\<**[**literal**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal7literalE)**\> get_sub_objects() const**

**inline** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **get_argument() const**

Convert the data to an argument.

## 5.2.3 Argument

**struct migraphx::internal::argument : public migraphx::internal::raw_data\<**[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE)**\>**

Arguments passed to instructions.

An argument can represent a raw buffer of data that either be referenced from another element or it can be owned by the argument.

**Public Functions**

**argument() = default**

**argument(const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&s)**

**template\<class F, long PrivateRequires__LINE_\_ = \_LINE_, typename std::enable_if\<(PrivateRequires__LINE_\_** **== \_LINE\_ && (migraphx::and_\<std::is_pointer\<decltype(std::declval\<**[**F**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXclNSt10is_pointerIDTclclNSt7declvalI1FEEEEEEEEEEEEEiE4typeEEN8migraphx8internal8argument8argumentE5shape1F)**\>()())\>{}\>{})), int\>::type = 0\>**  
**inline argument(**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **s**, [**F**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXclNSt10is_pointerIDTclclNSt7declvalI1FEEEEEEEEEEEEEiE4typeEEN8migraphx8internal8argument8argumentE5shape1F) **d)**

**template\<class T\>**  
**inline argument(**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **s**, [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal8argument8argumentE5shapeP1T) **\*d)**

**template\<class T\>**  
**inline argument(**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **s**, **std::shared_ptr\<**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal8argument8argumentE5shapeNSt10shared_ptrI1TEE)**\> d)**

**argument(**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **s**, **std::nullptr_t)**

**argument(const std::vector\<**[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argument8argumentERKNSt6vectorI8argumentEE)**\> \&args)**

**char \*data() const**

Provides a raw pointer to the data.

**bool empty() const**

Whether data is available.

**const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&get_shape() const**

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **reshape(const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&s) const**

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **copy() const**

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **share() const**

Make copy of the argument that is always sharing the data.

**std::vector\<**[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE)**\> get_sub_objects() const**

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **element(std::size_t i) const**

Return the ith element.

## 5.2.4 raw_data

**template\<class Derived\>**  
**struct migraphx::internal::raw_data : public migraphx::internal::raw_data_base**

Provides a base class for common operations with raw buffer.

For classes that handle a raw buffer of data, this will provide common operations such as equals, printing, and visitors. To use this class the derived class needs to provide a data() method to retrieve a raw pointer to the data, and get_shape method that provides the shape of the data.

**Public Functions**

**template\<class Visitor\>**  
**inline void visit_at(**[**Visitor**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal8raw_data8visit_atEv7VisitorNSt6size_tE) **v**, **std::size_t n = 0) const**

Visits a single data element at a certain index.

**Parameters**

-   **v** – A function which will be called with the type of data
-   **n** – The index to read from

**template\<class Visitor, class TupleVisitor\>**  
**inline void visit(**[**Visitor**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I00ENK8migraphx8internal8raw_data5visitEv7Visitor12TupleVisitor) **v**, **TupleVisitor tv) const**

**template\<class Visitor\>**  
**inline void visit(**[**Visitor**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal8raw_data5visitEv7Visitor) **v) const**

Visits the data.

This will call the visitor function with a tensor_view\<T\> based on the shape of the data.

**Parameters**

**v** – A function to be called with tensor_view\<T\>

**inline bool single() const**

Returns true if the raw data is only one element.

**template\<class T\>**  
**inline** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal8raw_data2atE1TNSt6size_tE) **at(std::size_t n = 0) const**

Retrieves a single element of data.

**Parameters n** – The index to retrieve the data from

**Template Parameter T** – The type of data to be retrieved

**Returns** The element as T

**inline auto_cast implicit() const**

Implicit conversion of raw data pointer.

**template\<class T\>**  
**inline tensor_view\<**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal8raw_data3getE11tensor_viewI1TEv)**\> get() const**

Get a tensor_view to the data.

**template\<class T\>**  
**inline** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal8raw_data4castEP1Tv) **\*cast() const**

Cast the data pointer.

**inline std::string to_string() const**

**Friends**

**template\<class Stream\> inline friend friend Stream & operator\<\< (Stream \&os, const Derived \&d)**

**struct auto_cast**

**Public Types**

**using is_data_ptr = bool_c\<(std::is_void\<T\>{} or std::is_same\<char, std::remove_cv_t\<T\>\>{} or std::is \_same\<unsigned char, std::remove_cv_t\<T\>\>{})\>**

**using get_data_type = std::conditional_t\<is_data_ptr\<T\>{}, float, T\>**

**Public Functions**

**template\<class T\>**  
**inline operator** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal8raw_data9auto_castcv1TEv)**()**

**template\<class T\>**  
**inline bool matches() const**

**template\<class T\>**  
**inline operator** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal8raw_data9auto_castcvP1TEv)**\*()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4I0EN8migraphx8internal8raw_data9auto_castcvP1TEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal8raw_data9auto_castcvP1TEv)

**Public Members**

**const** [**Derived**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal8raw_dataE) **\*self**

## 5.2.5 Tensor_view

**template\<class T\>**  
**struct migraphx::internal::tensor_view**

**Public Types**

**using value_type =** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE)[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view10value_typeE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view10value_typeE)

**using iterator = basic_iota_iterator\<tensor_view_iterator_read\<**[**tensor_view**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE)**\<**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE)**\>\>, std::size_t\>**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view8iteratorE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view8iteratorE)

**using const_iterator = basic_iota_iterator\<tensor_view_iterator_read\<const** [**tensor_view**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE)**\<**[**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE)**\>\>, std::size_t\>**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view14const_iteratorE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view14const_iteratorE)

**Public Functions**

**inline tensor_view()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view11tensor_viewEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view11tensor_viewEv)

**inline tensor_view(**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **s**, [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\*d)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view11tensor_viewE5shapeP1T](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view11tensor_viewE5shapeP1T)

**inline const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&get_shape() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4NK8migraphx8internal11tensor_view9get_shapeEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4NK8migraphx8internal11tensor_view9get_shapeEv)

**inline bool empty() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4NK8migraphx8internal11tensor_view5emptyEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4NK8migraphx8internal11tensor_view5emptyEv)

**inline std::size_t size() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4NK8migraphx8internal11tensor_view4sizeEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4NK8migraphx8internal11tensor_view4sizeEv)

**inline** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\*data()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view4dataEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view4dataEv)

**inline const** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\*data() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4NK8migraphx8internal11tensor_view4dataEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4NK8migraphx8internal11tensor_view4dataEv)

**template\<class ...Ts, long PrivateRequires__LINE_\_ = \_LINE_, typename std::enable_if\<(PrivateRequires__LINE_\_** **== \_LINE\_ && (migraphx::and_\<std::is_integral\<**[**Ts**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4IDp_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IJXclNSt11is_integralI2TsEEEEEEEEEiE4typeEENK8migraphx8internal11tensor_viewclERK1TDp2Ts)**\>{}...\>{})), int\>::type = 0z**  
**inline const** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&operator()(**[**Ts**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4IDp_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IJXclNSt11is_integralI2TsEEEEEEEEEiE4typeEENK8migraphx8internal11tensor_viewclERK1TDp2Ts)**... xs) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4IDp_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IJXclNSt11is_integralI2TsEEEEEEEEEiE4typeEENK8migraphx8internal11tensor_viewclERK1TDp2Ts](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4IDp_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IJXclNSt11is_integralI2TsEEEEEEEEEiE4typeEENK8migraphx8internal11tensor_viewclERK1TDp2Ts)

**template\<class ...Ts, long PrivateRequires__LINE_\_ = \_LINE_, typename std::enable_if\<(**[**PrivateRequires__LINE_\_**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4IDp_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IJXclNSt11is_integralI2TsEEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1TDp2Ts) **== \_LINE\_ && (migraphx::and_\<std::is_integral\<**[**Ts**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4IDp_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IJXclNSt11is_integralI2TsEEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1TDp2Ts)**\>{}...\>{})), int\>::type = 0\>**  
**inline** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&operator()(**[**Ts**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4IDp_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IJXclNSt11is_integralI2TsEEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1TDp2Ts)**... xs)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4IDp_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IJXclNSt11is_integralI2TsEEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1TDp2Ts](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4IDp_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IJXclNSt11is_integralI2TsEEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1TDp2Ts)

**template\<class Iterator, long PrivateRequires__LINE_\_ = \_LINE_, typename std::enable_if\<(PrivateRequires__LINE_\_** **== \_LINE\_ && (migraphx::and_\<not std::is_integral\<**[**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEENK8migraphx8internal11tensor_viewclERK1T8Iterator8Iterator)**\>{}\>{})), int\>::type = 0\>**  
**inline const** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&operator()(**[**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEENK8migraphx8internal11tensor_viewclERK1T8Iterator8Iterator) **start**, [**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEENK8migraphx8internal11tensor_viewclERK1T8Iterator8Iterator) **last) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEENK8migraphx8internal11tensor_viewclERK1T8Iterator8Iterator](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEENK8migraphx8internal11tensor_viewclERK1T8Iterator8Iterator)

**template\<class Iterator, long PrivateRequires__LINE_\_ = \_LINE_, typename std::enable_if\<(**[**PrivateRequires__LINE_\_**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1T8Iterator8Iterator) **== \_LINE\_ && (migraphx::and_\<not std::is_integral\<**[**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1T8Iterator8Iterator)**\>{}\>{})), int\>::type = 0\>**  
**inline** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&operator()(**[**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1T8Iterator8Iterator) **start**, [**Iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1T8Iterator8Iterator) **last)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1T8Iterator8Iterator](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0_l_NSt9enable_ifIXaaeq23PrivateRequires__LINE__8__LINE__clN8migraphx4and_IXntclNSt11is_integralI8IteratorEEEEEEEEiE4typeEEN8migraphx8internal11tensor_viewclER1T8Iterator8Iterator)

**inline** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&operator[](std::size_t i)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_viewixENSt6size_tE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_viewixENSt6size_tE)

**inline const** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&operator[](std::size_t i) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4NK8migraphx8internal11tensor_viewixENSt6size_tE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4NK8migraphx8internal11tensor_viewixENSt6size_tE)

**inline** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&front()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view5frontEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view5frontEv)

**inline const** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&front() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4NK8migraphx8internal11tensor_view5frontEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4NK8migraphx8internal11tensor_view5frontEv)

**inline** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&back()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view4backEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view4backEv)

**inline const** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE) **\&back() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4NK8migraphx8internal11tensor_view4backEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4NK8migraphx8internal11tensor_view4backEv)

**inline** [**iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view8iteratorE) **begin()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view5beginEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view5beginEv)

**inline** [**iterator**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view8iteratorE) **end()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4N8migraphx8internal11tensor_view3endEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal11tensor_view3endEv)

**inline const_iterator begin() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4NK8migraphx8internal11tensor_view5beginEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4NK8migraphx8internal11tensor_view5beginEv)

**inline const_iterator end() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4NK8migraphx8internal11tensor_view3endEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4NK8migraphx8internal11tensor_view3endEv)

**template\<class U =** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0EN8migraphx8internal11tensor_viewE)**\>**  
**inline std::vector\<**[**U**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal11tensor_view9to_vectorENSt6vectorI1UEEv)**\> to_vector() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html\#_CPPv4I0ENK8migraphx8internal11tensor_view9to_vectorENSt6vectorI1UEEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4I0ENK8migraphx8internal11tensor_view9to_vectorENSt6vectorI1UEEv)

**Friends**

**inline friend friend std::ostream & operator\<\< (std::ostream \&os, const tensor_view\< T \> \&x)**

# 5.3 Program

## 5.3.1 Instruction

**struct migraphx::internal::instruction**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instructionE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instructionE)

**Public Functions**

**inline instruction()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction11instructionEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction11instructionEv)

**instruction(**[**operation**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/operators.html#_CPPv4N8migraphx8internal9operationE) **o**, [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **r**, **std::vector\<**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE)**\> args)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction11instructionE9operation5shapeNSt6vectorI15instruction_refEE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction11instructionE9operation5shapeNSt6vectorI15instruction_refEE)

**instruction(**[**operation**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/operators.html#_CPPv4N8migraphx8internal9operationE) **o**, [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **r**, **std::vector\<**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE)**\> args**, **std::vector\<module_ref\> modules)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction11instructionE9operation5shapeNSt6vectorI15instruction_refEENSt6vectorI10module_refEE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction11instructionE9operation5shapeNSt6vectorI15instruction_refEENSt6vectorI10module_refEE)

**instruction(**[**literal**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal7literalE) **l)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction11instructionE7literal](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction11instructionE7literal)

**void replace(**[**operation**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/operators.html#_CPPv4N8migraphx8internal9operationE) **o)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction7replaceE9operation](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction7replaceE9operation)

**void recompute_shape()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction15recompute_shapeEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction15recompute_shapeEv)

**void clear_arguments()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction15clear_argumentsEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction15clear_argumentsEv)

**bool valid(instruction_ref** **start**, **bool check_order = false) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction5validE15instruction_refb](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction5validE15instruction_refb)

**bool valid() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction5validEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction5validEv)

[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **get_shape() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction9get_shapeEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction9get_shapeEv)

**const** [**literal**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal7literalE) **\&get_literal() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction11get_literalEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction11get_literalEv)

**const** [**operation**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/operators.html#_CPPv4N8migraphx8internal9operationE) **\&get_operator() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction12get_operatorEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction12get_operatorEv)

**std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction4nameEv)

**const std::vector\<instruction_ref\> \&inputs() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction6inputsEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction6inputsEv)

**const std::vector\<module_ref\> \&module_inputs() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction13module_inputsEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction13module_inputsEv)

**const std::vector\<instruction_ref\> \&outputs() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction7outputsEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction7outputsEv)

**void add_output(instruction_ref ins)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction10add_outputE15instruction_ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction10add_outputE15instruction_ref)

**template\<class T\>**  
**inline void remove_output(const** [**T**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4I0EN8migraphx8internal11instruction13remove_outputEvRK1T) **\&ins)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4I0EN8migraphx8internal11instruction13remove_outputEvRK1T](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4I0EN8migraphx8internal11instruction13remove_outputEvRK1T)

**bool can_eval() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction8can_evalEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction8can_evalEv)

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **eval(bool check_eval = true) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction4evalEb](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction4evalEb)

**void finalize(context \&ctx)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction8finalizeER7context](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction8finalizeER7context)

**void set_normalized(bool value = true)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction14set_normalizedEb](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction14set_normalizedEb)

**bool is_normalized() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction13is_normalizedEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction13is_normalizedEv)

**bool need_normalization() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction18need_normalizationEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction18need_normalizationEv)

[**operation**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/operators.html#_CPPv4N8migraphx8internal9operationE) **normalized_operator() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction19normalized_operatorEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction19normalized_operatorEv)

**void debug_print() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal11instruction11debug_printEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal11instruction11debug_printEv)

**Public Static Functions**

**static void replace_refs(**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **ins**, **const std::unordered_map\<**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE)**,** [**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE)**\> \&map_insts**, **const std::unordered_map\<module_ref, module_ref\> \&map_mods)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction12replace_refsE15instruction_refRKNSt13unordered_mapI15instruction_ref15instruction_refEERKNSt13unordered_mapI10module_ref10module_refEE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction12replace_refsE15instruction_refRKNSt13unordered_mapI15instruction_ref15instruction_refEERKNSt13unordered_mapI10module_ref10module_refEE)

**static void backreference(instruction_ref ref)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction13backreferenceE15instruction_ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction13backreferenceE15instruction_ref)

**static void replace_argument(**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **ins**, [**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **old**, [**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **new_ins)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction16replace_argumentE15instruction_ref15instruction_ref15instruction_ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction16replace_argumentE15instruction_ref15instruction_ref15instruction_ref)

**static void replace_mod_argument(**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **ins**, **module_ref old**, **module_ref new_mod)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction20replace_mod_argumentE15instruction_ref10module_ref10module_ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction20replace_mod_argumentE15instruction_ref10module_ref10module_ref)

**static void replace(**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **ins**, [**operation**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/operators.html#_CPPv4N8migraphx8internal9operationE) **o**, **const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&r**, **std::vector\<**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE)**\> args)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction7replaceE15instruction_ref9operationRK5shapeNSt6vectorI15instruction_refEE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction7replaceE15instruction_ref9operationRK5shapeNSt6vectorI15instruction_refEE)

**static void replace(**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **ins**, [**operation**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/operators.html#_CPPv4N8migraphx8internal9operationE) **o**, **const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&r**, **std::vector\<**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE)**\> args**, **std::vector\<module_ref\> module_args)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction7replaceE15instruction_ref9operationRK5shapeNSt6vectorI15instruction_refEENSt6vectorI10module_refEE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction7replaceE15instruction_ref9operationRK5shapeNSt6vectorI15instruction_refEENSt6vectorI10module_refEE)

**static** [**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **get_output_alias(**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **ins**, **bool shallow = false)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction16get_output_aliasE15instruction_refb](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction16get_output_aliasE15instruction_refb)

**static void print(std::ostream \&os**, [**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **ins**, **const std::unordered_map\<**[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE)**, std::string\> \&names)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal11instruction5printERNSt7ostreamE15instruction_refRKNSt13unordered_mapI15instruction_refNSt6stringEEE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal11instruction5printERNSt7ostreamE15instruction_refRKNSt13unordered_mapI15instruction_refNSt6stringEEE)

**Friends**

**friend friend bool operator== (const instruction \&i, instruction_ref ref)**

**friend friend bool operator== (const instruction \&x, const instruction \&y)**

**friend friend bool operator!= (const instruction \&x, const instruction \&y)**

**friend friend bool operator== (instruction_ref ref, const instruction \&i)**

**friend friend bool operator!= (const instruction \&i, instruction_ref ref)**

**friend friend bool operator!= (instruction_ref ref, const instruction \&i)**

## 5.3.2 Instruction_ref

**type migraphx::internal::instruction_ref**

References an instruction in the program.

## 5.3.3 Program

**struct migraphx::internal::program**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7programE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7programE)

Stores the instruction stream.

**Public Functions**

**program()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program7programEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program7programEv)

**program(**[**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program7programERR7program)**&&) noexcept**

**program(const** [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program7programERK7program)**&)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program7programERK7program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program7programERK7program)

[**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7programE) **\&operator=(**[**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7programE)**)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7programaSE7program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7programaSE7program)

**\~program() noexcept**

**std::vector\<std::string\> get_parameter_names() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program19get_parameter_namesEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program19get_parameter_namesEv)

[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **get_parameter_shape(std::string name) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program19get_parameter_shapeENSt6stringE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program19get_parameter_shapeENSt6stringE)

[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **get_parameter(std::string name) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program13get_parameterENSt6stringE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program13get_parameterENSt6stringE)

**std::unordered_map\<std::string,** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE)**\> get_parameter_shapes() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program20get_parameter_shapesEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program20get_parameter_shapesEv)

**std::vector\<**[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE)**\> eval(parameter_map params) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program4evalE13parameter_map](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program4evalE13parameter_map)

**std::size_t size() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program4sizeEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program4sizeEv)

**std::vector\<**[**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE)**\> get_output_shapes() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program17get_output_shapesEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program17get_output_shapesEv)

**context \&get_context() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program11get_contextEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program11get_contextEv)

[**instruction_ref**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal15instruction_refE) **validate() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program8validateEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program8validateEv)

**void compile(const** [**target**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4N8migraphx8internal6targetE) **\&t**, **compile_options options = compile_options{})**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program7compileERK6target15compile_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program7compileERK6target15compile_options)

**bool is_compiled() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program11is_compiledEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program11is_compiledEv)

**void finalize()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program8finalizeEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program8finalizeEv)

**void perf_report(std::ostream \&os**, **std::size_t n**, **parameter_map params**, **std::size_t batch = 1) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program11perf_reportERNSt7ostreamENSt6size_tE13parameter_mapNSt6size_tE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program11perf_reportERNSt7ostreamENSt6size_tE13parameter_mapNSt6size_tE)

**void mark(const parameter_map \&params**, **marker &&m)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program4markERK13parameter_mapRR6marker](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program4markERK13parameter_mapRR6marker)

**value to_value() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program8to_valueEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program8to_valueEv)

**void from_value(const value \&v)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program10from_valueERK5value](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program10from_valueERK5value)

**void debug_print() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program11debug_printEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program11debug_printEv)

**void debug_print(instruction_ref ins) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program11debug_printE15instruction_ref](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program11debug_printE15instruction_ref)

**void print(std::unordered_map\<instruction_ref, std::string\> \&names**, **const std::function\<void(instruction_ref, std::unordered_map\<instruction_ref, std::string\>)\> \&print_func) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program5printERNSt13unordered_mapI15instruction_refNSt6stringEEERKNSt8functionIFv15instruction_refNSt13unordered_mapI15instruction_refNSt6stringEEEEEE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program5printERNSt13unordered_mapI15instruction_refNSt6stringEEERKNSt8functionIFv15instruction_refNSt13unordered_mapI15instruction_refNSt6stringEEEEEE)

**void print_graph(std::ostream \&os**, **bool brief = false) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program11print_graphERNSt7ostreamEb](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program11print_graphERNSt7ostreamEb)

**void print_cpp(std::ostream \&os) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program9print_cppERNSt7ostreamE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program9print_cppERNSt7ostreamE)

**void dry_run(parameter_map params) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program7dry_runE13parameter_map](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program7dry_runE13parameter_map)

**void annotate(std::ostream \&os**, **const std::function\<void(instruction_ref)\> \&a) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program8annotateERNSt7ostreamERKNSt8functionIFv15instruction_refEEE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program8annotateERNSt7ostreamERKNSt8functionIFv15instruction_refEEE)

[**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7programE) **\&sort()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program4sortEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program4sortEv)

**module \*create_module(const std::string \&name)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program13create_moduleERKNSt6stringE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program13create_moduleERKNSt6stringE)

**module \*get_module(const std::string \&name)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program10get_moduleERKNSt6stringE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program10get_moduleERKNSt6stringE)

**const module \*get_module(const std::string \&name) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program10get_moduleERKNSt6stringE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program10get_moduleERKNSt6stringE)

**module \*get_main_module()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program15get_main_moduleEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program15get_main_moduleEv)

**const module \*get_main_module() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program15get_main_moduleEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program15get_main_moduleEv)

**std::vector\<const module\*\> get_modules() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4NK8migraphx8internal7program11get_modulesEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4NK8migraphx8internal7program11get_modulesEv)

**std::vector\<module\*\> get_modules()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program11get_modulesEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program11get_modulesEv)

**void remove_module(const std::string \&name)**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program13remove_moduleERKNSt6stringE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program13remove_moduleERKNSt6stringE)

**void remove_unused_modules()**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal7program21remove_unused_modulesEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7program21remove_unused_modulesEv)

**Friends**

**friend friend std::ostream & operator\<\< (std::ostream \&os, const program \&p)**

**friend friend bool operator== (const program \&x, const program \&y)**

**inline friend friend bool operator!= (const program \&x, const program \&y)**

## 5.3.4 Parse_onnx

[**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7programE) **migraphx::internal::parse_onnx(const std::string \&name**, **const** [**onnx_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal12onnx_optionsE)**& =** [**onnx_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal12onnx_optionsE)**{})**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal10parse_onnxERKNSt6stringERK12onnx_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal10parse_onnxERKNSt6stringERK12onnx_options)

Create a program from an onnx file.

## 5.3.5 Parse_tf

[**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7programE) **migraphx::internal::parse_tf(const std::string \&name**, **const** [**tf_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal10tf_optionsE) **\&options =** [**tf_options**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal10tf_optionsE)**{})**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal8parse_tfERKNSt6stringERK10tf_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal8parse_tfERKNSt6stringERK10tf_options)

Create a program from a tf pb file (default is nhwc format)

## 5.3.6 Onnx_options

**struct migraphx::internal::onnx_options**

struct to pass in onnx options to parser

**Public Members**

**std::size_t default_dim_value = 1** [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal12onnx_options17default_dim_valueE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal12onnx_options17default_dim_valueE)

default batch size to use (if not specified in onnx file)

**std::unordered_map\<std::string, std::vector\<std::size_t\>\> map_input_dims = {}**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal12onnx_options14map_input_dimsE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal12onnx_options14map_input_dimsE)

Explicitly specify the dims of an input.

**bool skip_unknown_operators = false**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal12onnx_options22skip_unknown_operatorsE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal12onnx_options22skip_unknown_operatorsE)

Continue parsing onnx file if an unknown operator is found.

**bool print_program_on_error = false** [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal12onnx_options22print_program_on_errorE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal12onnx_options22print_program_on_errorE)

Print program if an error occurs.

**int64_t max_loop_iterations = 10**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal12onnx_options19max_loop_iterationsE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal12onnx_options19max_loop_iterationsE)

Max iter num for the loop operator.

## 5.3.7 Tf_options

**struct migraphx::internal::tf_options**

struct to pass in tf options to parser

**Public Members**

**bool is_nhwc = false**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal10tf_options7is_nhwcE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal10tf_options7is_nhwcE)

**unsigned int batch_size = 1**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal10tf_options10batch_sizeE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal10tf_options10batch_sizeE)

**std::unordered_map\<std::string, std::vector\<std::size_t\>\> map_input_dims = {}**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html\#_CPPv4N8migraphx8internal10tf_options14map_input_dimsE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal10tf_options14map_input_dimsE)

Explicitly specify the dims of an input.

**std::vector\<std::string\> output_node_names = {}**

# 5.4 Targets

## 5.4.1 Target

**struct migraphx::internal::target**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4N8migraphx8internal6targetE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4N8migraphx8internal6targetE)

An interface for a compilation target.

**Public Functions**

**std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal6target4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal6target4nameEv)

A unique name used to identify the target.

**std::vector\<**[**pass**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4N8migraphx8internal4passE)**\> get_passes(context \&ctx**, **const compile_options \&options) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal6target10get_passesER7contextRK15compile_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal6target10get_passesER7contextRK15compile_options)

The transformation pass to be run during compilation.

**Parameters**

-   **ctx** – This is the target-dependent context that is created by get_context
-   **options** – Compiling options passed in by the user

    **Returns:** The passes to be ran

**context get_context() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal6target11get_contextEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal6target11get_contextEv)

Construct a context for the target.

**Returns:** The context to be used during compilation and execution.

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **copy_to(const** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **\&arg) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal6target7copy_toERK8argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal6target7copy_toERK8argument)

copy an argument to the current target.

**Parameters: arg** – Input argument to be copied to the target

**Returns:** Argument in the target.

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **copy_from(const** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **\&arg) const** [https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal6target9copy_fromERK8argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal6target9copy_fromERK8argument)

copy an argument from the current target.

**Parameters: arg** – Input argument to be copied from the target

**Returns:** Argument in the host.

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **allocate(const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&s) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal6target8allocateERK5shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal6target8allocateERK5shape)

Allocate an argument based on the input shape.

**Parameters: s** – Shape of the argument to be allocated in the target

**Returns** Allocated argument in the target.

## 5.4.2 gpu::target

**struct migraphx::internal::gpu::target**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4N8migraphx8internal3gpu6targetE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4N8migraphx8internal3gpu6targetE)

**Public Functions**

**std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3gpu6target4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3gpu6target4nameEv)

**std::vector\<**[**pass**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4N8migraphx8internal4passE)**\> get_passes(migraphx::context \&gctx**, **const compile_options \&options) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3gpu6target10get_passesERN8migraphx7contextERK15compile_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3gpu6target10get_passesERN8migraphx7contextERK15compile_options)

**migraphx::context get_context() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3gpu6target11get_contextEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3gpu6target11get_contextEv)

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **copy_to(const** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **\&arg) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3gpu6target7copy_toERK8argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3gpu6target7copy_toERK8argument)

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **copy_from(const** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **\&arg) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3gpu6target9copy_fromERK8argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3gpu6target9copy_fromERK8argument)

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **allocate(const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&s) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3gpu6target8allocateERK5shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3gpu6target8allocateERK5shape)

## 5.4.3 cpu::target

**struct migraphx::internal::cpu::target**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4N8migraphx8internal3cpu6targetE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4N8migraphx8internal3cpu6targetE)

**Public Functions**

**std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3cpu6target4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3cpu6target4nameEv)

**std::vector\<**[**pass**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4N8migraphx8internal4passE)**\> get_passes(migraphx::context \&gctx**, **const compile_options&) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3cpu6target10get_passesERN8migraphx7contextERK15compile_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3cpu6target10get_passesERN8migraphx7contextERK15compile_options)

**inline migraphx::context get_context() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3cpu6target11get_contextEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3cpu6target11get_contextEv)

**inline** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **copy_to(const** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **\&arg) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3cpu6target7copy_toERK8argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3cpu6target7copy_toERK8argument)

**inline** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **copy_from(const** [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **\&arg) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3cpu6target9copy_fromERK8argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3cpu6target9copy_fromERK8argument)

[**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal8argumentE) **allocate(const** [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/data.html#_CPPv4N8migraphx8internal5shapeE) **\&s) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html\#_CPPv4NK8migraphx8internal3cpu6target8allocateERK5shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/targets.html#_CPPv4NK8migraphx8internal3cpu6target8allocateERK5shape)

# 5.5 Passes

## 5.5.1 Pass

**struct migraphx::internal::pass**

An interface for applying a transformation to the instructions in a program

**Public Functions**

**std::string name() const**

A unique name used to identify the pass.

**void apply(module_pass_manager \&mpm) const**

Run the pass on the module.

**void apply(module \&m) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal4pass5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal4pass5applyER6module)

**void apply(**[**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7programE) **\&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal4pass5applyER7program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal4pass5applyER7program)

Run the pass on the program.

## 5.5.2 Dead_code_elimination

**struct migraphx::internal::dead_code_elimination**

Remove instructions where the output is not used.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal21dead_code_elimination4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal21dead_code_elimination4nameEv)

**void apply(module \&m) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal21dead_code_elimination5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal21dead_code_elimination5applyER6module)

**void apply(**[**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/program.html#_CPPv4N8migraphx8internal7programE) **\&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal21dead_code_elimination5applyER7program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal21dead_code_elimination5applyER7program)

## 5.5.3 Eliminate_common_subexpression

**struct migraphx::internal::eliminate_common_subexpression**

Remove identical instructions.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal30eliminate_common_subexpression4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal30eliminate_common_subexpression4nameEv)

**void apply(module \&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal30eliminate_common_subexpression5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal30eliminate_common_subexpression5applyER6module)

## 5.5.4 Eliminate_concat

**struct migraphx::internal::eliminate_concat**

Remove concat operators by having each operator can write to different chunk of memory.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal16eliminate_concat4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal16eliminate_concat4nameEv)

**void apply(module \&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal16eliminate_concat5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal16eliminate_concat5applyER6module)

**Public Members**

**concat_optimization concat_opt**

## 5.5.5 Eliminate_contiguous

**struct migraphx::internal::eliminate_contiguous**

Remove contiguous instructions by checking if the operator can use non-standard shapes.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal20eliminate_contiguous4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal20eliminate_contiguous4nameEv)

**void apply(module \&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal20eliminate_contiguous5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal20eliminate_contiguous5applyER6module)

**Public Members**

**std::string op_name**

## 5.5.6 Eliminate_identity

**struct migraphx::internal::eliminate_identity**

Remove identity instructions. Currently when used as the last pass, it will preserve the semantics of previous program state, therefore dead code elimination should not be used afterwards.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal18eliminate_identity4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal18eliminate_identity4nameEv)

**void apply(module \&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal18eliminate_identity5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal18eliminate_identity5applyER6module)

## 5.5.7 Eliminate_pad

**struct migraphx::internal::eliminate_pad**

Remove pads if they can be written as an attribute to another op (im2col, convolution, pooling)

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal13eliminate_pad4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal13eliminate_pad4nameEv)

**void apply(module \&m) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal13eliminate_pad5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal13eliminate_pad5applyER6module)

## 5.5.8 Propagate_constant

**struct migraphx::internal::propagate_constant**

Replace instructions which take all literals with a literal of the computation.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal18propagate_constant4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal18propagate_constant4nameEv)

**void apply(module \&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal18propagate_constant5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal18propagate_constant5applyER6module)

## 5.5.9 Rewrite_batchnorm

**struct migraphx::internal::rewrite_batchnorm**

Rewrite batchnorm to a multiply and add.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal17rewrite_batchnorm4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal17rewrite_batchnorm4nameEv)

**void apply(module \&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal17rewrite_batchnorm5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal17rewrite_batchnorm5applyER6module)

## 5.5.10 Rewrite_rnn

**struct migraphx::internal::rewrite_rnn**

Rewrite rnn to gemm and add.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal11rewrite_rnn4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal11rewrite_rnn4nameEv)

**void apply(module \&prog) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal11rewrite_rnn5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal11rewrite_rnn5applyER6module)

## 5.5.11 Schedule

**struct migraphx::internal::schedule**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4N8migraphx8internal8scheduleE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4N8migraphx8internal8scheduleE)

Schedule instructions for concurrent execution

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal8schedule4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal8schedule4nameEv)

**void apply(module \&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal8schedule5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal8schedule5applyER6module)

**Public Members**

**schedule_model model = {}**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4N8migraphx8internal8schedule5modelE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4N8migraphx8internal8schedule5modelE)

**bool enable = true**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4N8migraphx8internal8schedule6enableE](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4N8migraphx8internal8schedule6enableE)

## 5.5.12 Simplify_algebra

**struct migraphx::internal::simplify_algebra**

Simplify many algebraic instructions to more efficient versions.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal16simplify_algebra4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal16simplify_algebra4nameEv)

**void apply(module \&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal16simplify_algebra5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal16simplify_algebra5applyER6module)

## 5.5.13 Simplify_reshapes

**struct migraphx::internal::simplify_reshapes**

Eliminate redundant reshapes.

**Public Functions**

**inline std::string name() const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal17simplify_reshapes4nameEv](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal17simplify_reshapes4nameEv)

**void apply(module \&p) const**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html\#_CPPv4NK8migraphx8internal17simplify_reshapes5applyER6module](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/pass.html#_CPPv4NK8migraphx8internal17simplify_reshapes5applyER6module)

# 5.6 Matchers

## 5.6.1 Introduction

The matchers provide a way compose several predicates together. Many of the matchers can be composed so that m(m1, m2) will first check that m matches and then it will check that m1 and m2 will match.

The most commonly-used matcher is the name matcher. It will match the instruction that have the operator that is equal to the name specified:

**auto** match_sum = name("sum");

This will find sum operators. We can also find sum operators which the output is standard_shape:

auto match_sum = name(“sum”)(standard_shape());

## 5.6.2 Arguments

We also want to match arguments to the instructions as well. One way, is to match each argument using the arg matcher:

**auto** match_sum = name("sum")(arg(0)(name("@literal"), arg(1)(name("@literal"))));

This will match a sum operator with the two arguments that are literals. Of course, instead of writing arg(0) and arg(1) everytime, the args matcher can be used:

**auto** match_sum = name("sum")(args(name("@literal"), name("@literal")));

## 5.6.3 Binding

As we traverse through the instructions we may want reference some of the instructions we find along the way. We can do this by calling .bind:

**auto** match_sum = name("sum")(args(

name("@literal").bind("one"),

name("@literal").bind("two")

)).bind("sum");

This will associate the instruction to a name that can be read from the matcher_result when it matches.

## 5.6.4 Finding matches

Finally, when you want to use the matchers to find instructions a callback object can be written which has the matcher and an apply function which will take the matcher_result when the match is found:

**struct** **match_find_sum**

{

**auto** matcher() **const** { **return** name("sum"); }

void apply(program& p, matcher_result r) **const**

{

*// Do something with the result*

}

};

find_matches(prog, match_find_sum{});

## 5.6.5 Creating matchers

There are several ways to create matchers. The macros MIGRAPH_BASIC_MATCHER and MIGRAPH_PRED_MATCHER help with creating matchers. For example, we can create a matcher for shapes that are broadcasted:

MIGRAPH_PRED_MATCHER(broadcasted_shape, instruction_ref ins)

{

**return** ins-\>get_shape().broadcasted();

}

If we want parameters to the predicate, then we will need to use the make_basic_pred_matcher to create the matcher. For example, here is how we would create a matcher to check the number of dimensions of the shape:

**inline** **auto** number_of_dims(std::size_t n)

{

**return** make_basic_pred_matcher([=](instruction_ref ins) {

**return** ins-\>get_shape().lens().size() == n;

});

}

# 5.7 Tools

## 5.7.1 roctx.py

MIGraphX driver provides **roctx** command which can be used with **rocprof** binary to get marker timing information for each MIGraphX operator. In order to help user to process timing information, rocTX helper script is provided at **tools/roctx.py**. The **roctx.py** helper script provides two main functionality: **run** and **parse**. Available knobs and usage are given below:

**Usage**: roctx.py [-h] [--json-path json_path] [--out out]

[--study-name study-name] [--repeat repeat] [--parse]

[--run run] [--debug]

\--run

Runs **migraphx-driver roctx** command and given **migraphx-driver** knobs, and then parses the results, providing GPU kernel timing information. MIGraphX knobs can be given via a string to **--run** knob. Please see the examples below.

**--parse**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html\#cmdoption-parse](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html#cmdoption-parse)

Given **--json-path**, parses JSON file and provides GPU kernel timing information.

**--out**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html\#cmdoption-out](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html#cmdoption-out)

Output folder

**--study-name**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html\#cmdoption-study-name](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html#cmdoption-study-name)

Optional. Allows user to name a study for easier interpretation. Defaults to timestamp.

**--repeat**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html\#cmdoption-repeat](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html#cmdoption-repeat)

Number of iterations. Set to **2** by default.

**--debug**[https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html\#cmdoption-debug](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/dev/tools.html#cmdoption-debug)

Provides additional debug information related to data. Only use for debugging purposes.

**Examples:**

**Running inference with rocTX for a given ONNX file:**

python roctx.py --run '--onnx --gpu fcn-resnet50-11.onnx' --out output_folder --repeat 5

After a run, similar to output given below is expected at terminal. The output will provide **SUM**, **MIN**, **MAX** and **COUNT** information for each kernel executed for a given model. Average total time is also provided. There are three files provided for reference:

1.  **OUTPUT CSV FILE** provides a summary of the run, providing utilized MIGraphX knobs and related kernel timing information
2.  **KERNEL TIMING DETAILS** provides the hotspot kernel timing information
3.  This will provide all output data related to all iterations executed during a run.

An example output:

![Table Description automatically generated](media/4e9cabfe12c52e917a4cfd626c3ae52f.png)

Hotspot kerel timing information:

![Text Description automatically generated](media/204c43b3f8b10086b0f6a59a93a554ba.png)

**Parsing an already existing JSON file:**

python roctx.py --parse --json-path ../trace.json
