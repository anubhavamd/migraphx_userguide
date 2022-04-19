1. Getting Started Guide for MIGraphX
=====================================

1.1. Introduction
=================

<span id="_Toc100742644" class="anchor"><span id="_Toc100742733"
class="anchor"></span></span>The MIGraphX execution provider uses AMD's
Deep Learning graph optimization engine to accelerate ONNX model on AMD
GPUs.

<span id="_Toc100742645" class="anchor"><span id="_Toc100742734"
class="anchor"></span></span>ONNX Runtime is an accelerator for machine
learning models with multi platform support and a flexible interface to
integrate with hardware-specific libraries. ONNX Runtime can be used
with models from PyTorch, Tensorflow/Keras, TFLite, scikit-learn, and
other frameworks.

<span id="_Toc100742646" class="anchor"><span id="_Toc100742735"
class="anchor"></span></span>The document also contains an Python User
guide, C++ user Guide, MIGraphX Driver and Contributor Guide.

Documentation Roadmap
---------------------

The following is a list of MIGraphX documents in the suggested reading
order:

> Getting Started Guide (this document): In this section we have
> introduce MIGraphX, ONNX Runtime.
>
> Python User Guide: In this section we will be defining different
> modules like shape, target, argument, save, load, etc.

C++ Reference: Describe modules like shape, argument, load, parse\_onnx,
etc.

MIGraphX Driver: Under this section we will cover modules like perf,
verify, roctx, etc.

> Contributor’s Guide: Provides detailed information about MIGraphX
> Fundamentals, datatypes, operators, targets, etc.

1.2. List of prerequisites
==========================

The following is a list of prerequisites required to build MIGraphX
source.

-   [*ROCm cmake
    modules*](https://github.com/RadeonOpenCompute/rocm-cmake) required

-   [*MIOpen*](https://github.com/ROCmSoftwarePlatform/MIOpen) for
    running on the GPU

-   [*rocBLAS*](https://github.com/ROCmSoftwarePlatform/rocBLAS) for
    running on the GPU

-   [*HIP*](https://github.com/ROCm-Developer-Tools/HIP) for running on
    the GPU

-   [*Protobuf*](https://github.com/google/protobuf) for
    reading [*onnx*](https://github.com/onnx/onnx) files

-   [*Half*](http://half.sourceforge.net/) - IEEE 754-based
    half-precision floating point library

-   [*pybind11*](https://pybind11.readthedocs.io/en/stable/) - for
    python bindings

-   [*JSON*](https://github.com/nlohmann/json) - for model serialization
    to json string format

-   [*MessagePack*](https://msgpack.org/index.html) - for model
    serialization to binary format

1.3. Installing pre-built packages
==================================

With ROCm installed correctly, MIGraphX binaries can be installed on
Ubuntu with the following command:

sudo apt update && sudo apt install -y migraphx

then the header files and libs are installed
under /opt/rocm-&lt;version&gt;, where &lt;version&gt; is the ROCm
version.

1.4. Building From Source
=========================

There are three ways to build the MIGraphX sources.

-   [*Use the ROCm build
    tool*](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-the-rocm-build-tool-rbuild)

> This approach
> uses [*rbuild*](https://github.com/RadeonOpenCompute/rbuild) to
> install the prerequisites and build the libs with just one command.

-   [*Use
    cmake*](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-cmake-to-build-migraphx)

> This approach uses a script to install the prerequisites, then use
> cmake to build the source.

-   [*Use
    docker*](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#use-docker)

> This approach builds a docker image with all prerequisites installed,
> then build the MIGraphX sources inside a docker container.

#### **1.4.1. Use the ROCm build tool [rbuild](https://github.com/RadeonOpenCompute/rbuild)**.

In this approach, we use
the [rbuild](https://github.com/RadeonOpenCompute/rbuild) build tool to
build MIGraphX. The specific steps are as follows:

1.  Install rocm-cmake, pip3, rocblas, and miopen-hip with the command

sudo apt update && sudo apt install -y rocm-cmake python3-pip rocblas
miopen-hip

1.  Install [*rbuild*](https://github.com/RadeonOpenCompute/rbuild) (sudo
    may be required here.)

pip3 install
https://github.com/RadeonOpenCompute/rbuild/archive/master.tar.gz

1.  Build MIGraphX source code

rbuild build -d depend -B build --cxx=/opt/rocm/llvm/bin/clang++

then all the prerequisites are in the folder depend, and MIGraphX is
built in the build directory.

Note that for ROCm3.7 and later releases, Ubuntu 18.04 or later releases
are needed. Upgrade to Ubuntu 18.04 is available at [Upgrade Ubuntu to
18.04](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/wiki/Upgrade-to-Ubuntu-18.04-for-ROCM3.7-or-later-releases)

Also note that you may meet the error of rbuild: command not found. It
is because rbuild is installed at \$HOME/.local/bin, which is not
in PATH. You can either export PATH as export
PATH=\$HOME/.local/bin:\$PATH to add the folder to PATH or add the
option --prefix /usr/local in the pip3 command when installing rbuild.

1.4.2. Use cmake to build MIGraphX
----------------------------------

If using this approach, we need to install the prerequisites, configure
the cmake, and then build the source.

##### Installing the prerequisites

For convenience, the prerequisites can be built automatically with
rbuild as:

rbuild build -d depend --cxx=/opt/rocm/llvm/bin/clang++

then all the prerequisites are in the folder depend, and they can be
used in the cmake configuration as -DCMAKE\_PREFIX\_PATH=depend.

If you have sudo access, as an alternative to the rbuild command, you
can install the prerequisites just like in the dockerfile by
calling ./tools/install\_prereqs.sh.

(Note that this script is for Ubuntu. By default, all prerequisites are
installed at the default location /usr/local and are accessible by all
users. For the default location, sudo is required to run the script. You
can also specify a location at which the prerequisites are installed
with ./tools/install\_prereqs.sh \$your\_loc.)

##### Building MIGraphX source and install libs

With the above prerequisites installed, we can build source as:

1.  Go to the project folder and create a build directory:

mkdir build

cd build

1.  Configure the cmake. If the prerequisites are installed at the
    default location /usr/local, the command is:

CXX=/opt/rocm/llvm/bin/clang++ cmake..

> Otherwise, you need to set -DCMAKE\_PREFIX\_PATH=\$your\_loc to
> configure the cmake.

1.  Build MIGraphX source code

make -j\$(nproc)

> Correctness can be verified as:

make -j\$(nproc) check

> MIGraphX libs can be installed as:

make install

1.4.3. Use docker
-----------------

The easiest way to setup the development environment is to use docker.
With the dockerfile, you can build a docker image as:

docker build -t migraphx.

Then to enter the developement environment use docker run:

docker run --device='/dev/kfd' --device='/dev/dri'
-v=\`pwd\`:/code/AMDMIGraphX -w /code/AMDMIGraphX --group-add video -it
migraphx

In the docker container, all the required prerequisites are already
installed, so users can just go to the folder /code/AMDMIGraphX and
follow the steps in the above [Build MIGraphX source and install
libs](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#building-migraphx-source-and-install-libs) section
to build MIGraphX source.c

2. Python User Guide
====================

2.1. Setting path and installing package
========================================

To use MIGraphX's Python module, please either set PYTHONPATH or
use .deb package as explained below:

-   Setting PYTHONPATH:

export PYTHONPATH=/opt/rocm/lib:\$PYTHONPATH

-   Creating and installing the package:

To create deb package:

make package

This will provide the path of .deb package.

To install:

dpkg -i &lt;path\_to\_deb\_file&gt;

2.2 Defining different modules in detail
========================================

2.2.1. Shape
------------

***class*migraphx.shape(*type***, ***lens***, ***strides=None*)**

> Describes the shape of a tensor. This includes size, layout, and data
> type/

**migraphx.type()**

> An integer that represents the type
>
> **Return type:** int

**migraphx.lens()**

> A list of the lengths of the shape
>
> **Return type:** list\[int\]

**migraphx.strides()**

> A list of the strides of the shape
>
> **Return type:** list\[int\]

**migraphx.elements()**

> The number of elements in the shape
>
> **Return type:** int

**migraphx.bytes()**

> The number of bytes the shape uses
>
> **Return type:** int

**migraphx.type\_size()**

> The number of bytes one element uses
>
> **Return type:** int

**migraphx.packed()**

> Returns true if the shape is packed.
>
> **Return type:** bool

**migraphx.transposed()**

> Returns true if the shape is transposed.
>
> **Return type:** bool

**migraphx.broadcasted()**

> Returns true if the shape is broadcasted.
>
> **Return type:** bool

**migraphx.standard()**

> Returns true if the shape is a standard shape. That is, the shape is
> both packed and not transposed.
>
> **Return type:** bool

**migraphx.scalar()**

> Returns true if all strides are equal to 0 (scalar tensor).
>
> **Return type:** bool

2.2.2. Argument
---------------

***class*migraphx.argument(*data*)**

> Construct an argument from a python buffer. This can include numpy
> arrays.

**migraphx.get\_shape()**

> Returns the shape of the argument.
>
> **Return type:** shape

**migraphx.tolist()**

> Convert the elements of the argument to a python list.
>
> **Return type:** list

**migraphx.generate\_argument(*s***, ***seed=0*)**

> Generate an argument with random data.

**Parameters:
s** ([*shape*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.shape))
– Shape of argument to generate.

> **seed** (*int*) – The seed used for random number generation

**Return type:**
[argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)

2.2.3. Target
-------------

***Class migraphx.target***

> This represents the compiliation target.

**migraphx.get\_target(*name*)**

> Constructs the target.
>
> **Parameters: name** (*str*) – The name of the target to construct.
> This can either be ‘gpu’ or ‘ref’.

**Return type:** target

2.2.4. Program
--------------

***class* migraphx.program**

Represents the computation graph to be compiled and run.

**migraphx.clone()**

> Make a copy of the program
>
> **Return type:**
> [*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

**migraphx.get\_parameter\_shapes()**

> Get the shapes of all the input parameters in the program.
>
> **Return type:**
> dict\[str, [*shape*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.shape)\]

**migraphx.get\_shape()**

> Get the shape of the final output of the program.
>
> **Return type:**
> [*shape*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.shape)

**migraphx.compile(*t***, ***offload\_copy=True***, ***fast\_math=True*)**

> Compiles the program for the target and optimizes it.
>
> **Parameters**

-   **t** ([*target*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.target))
    > – This is the target to compile the program for.

-   **offload\_copy** (*bool*) – For targets with offloaded memory(such
    > as the gpu), this will insert instructions during compilation to
    > copy the input parameters to the offloaded memory and to copy the
    > final result from the offloaded memory back to main memory.

-   **fast\_math** (*bool*) – Optimize math functions to use faster
    > approximate versions. There may be slight accuracy degredation
    > when enabled.

**migraphx.run(*params*)**

> Run the program.
>
> **Parameters:
> params** (*dict\[str, [argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)\]*)
> – This is a map of the input parameters which will be used when
> running the program.

**Returns:** The result of the last instruction.

**Return type:**
[*argument*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)

**migraphx.quantize\_fp16(*prog***, ***ins\_names=\['all'\]*)**

> Quantize the program to use fp16.
>
> **Parameters:
> prog** ([*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program))
> – Program to quantize.
>
> **ins\_names** (*list\[str\]*) – List of instructions to quantize.

**migraphx.quantize\_int8(*prog***, ***t***, ***calibration=\[\]***, ***ins\_names=\['dot', 'convolution'\]*)**

> Quantize the program to use int8.
>
> **Parameters**

-   **prog** ([*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program))
    > – Program to quantize.

-   **t** ([*target*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.target))
    > – Target that will be used to run the calibration data.

-   **calibration** (*list\[dict\[str, [argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.argument)\]\]*)
    > – Calibration data used to decide the parameters to the
    > int8 optimization.

-   **ins\_names** (*list\[str\]*) – List of instructions to quantize.

2.2.5. parse\_onnx
------------------

migraphx.parse\_onnx(filename, default\_dim\_value=1, map\_input\_dims={}, skip\_unknown\_operators=false, print\_program\_on\_error=false)

> Load and parse an onnx file.
>
> **Parameters**

-   **filename** (*str*) – Path to file.

-   **default\_dim\_value** (*str*) – default batch size to use (if not
    > specified in onnx file).

-   **map\_input\_dims** (*str*) – Explicitly specify the dims of
    > an input.

-   **skip\_unknown\_operators** (*str*) – Continue parsing onnx file if
    > an unknown operator is found.

-   **print\_program\_on\_error** (*str*) – Print program if an
    > error occurs.

> **Return type:**
> [*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

2.2.6. parse\_tf
----------------

**migraphx.parse\_tf(*filename***, ***is\_nhwc=True***, ***batch\_size=1*)**

> Load and parse an tensorflow protobuf file file.
>
> **Parameters**

-   **filename** (*str*) – Path to file.

-   **is\_nhwc** (*bool*) – Use nhwc as default format.

-   **batch\_size** (*str*) – default batch size to use (if not
    > specified in protobuf).

> **Return type:**
> [*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

2.2.7. Load
-----------

**migraphx.load(*filename***, ***format='msgpack'*)**

> Load a MIGraphX program
>
> **Parameters**

-   **filename** (*str*) – Path to file.

-   **format** (*str*) – Format of file. Valid options are msgpack
    > or json.

**Return type:**
[*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program)

2.2.8. Save
-----------

**migraphx.save(*p***, ***filename***, ***format='msgpack'*)**

> Save a MIGraphX program
>
> **Parameters**

-   **p** ([*program*](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/py.html#migraphx.program))
    > – Program to save.

-   **filename** (*str*) – Path to file.

-   **format** (*str*) – Format of file. Valid options are msgpack
    > or json.

3. C++ User Guide
=================

3.1 Defining different modules in detail
========================================

3.1.1 Shape
-----------

***enum* migraphx\_shape\_datatype\_t**

An enum to represent the different data type inputs.

*Values:*

***enumerator* migraphx\_shape\_tuple\_type**

***enumerator* migraphx\_shape\_bool\_type**

***enumerator* migraphx\_shape\_half\_type**

***enumerator* migraphx\_shape\_float\_type**

***enumerator* migraphx\_shape\_double\_type**

***enumerator* migraphx\_shape\_uint8\_type**

***enumerator* migraphx\_shape\_int8\_type**

***enumerator* migraphx\_shape\_uint16\_type**

***enumerator* migraphx\_shape\_int16\_type**

***enumerator* migraphx\_shape\_int32\_type**

***enumerator* migraphx\_shape\_int64\_type**

***enumerator* migraphx\_shape\_uint32\_type**

***enumerator* migraphx\_shape\_uint64\_type**

***struct* migraphx::shape : *public* migraphx::handle\_base&lt;&gt;**

Describe shape of tensor.

A shape consists of a data type, lengths of multi-dimension tensor, and
strides

**Public Functions**

***inline* shape()**

***inline* shape(*const* migraphx\_shape \*p)**

***inline* shape(migraphx\_shape \*p**, **own)**

***inline* shape(migraphx\_shape \*p**, **borrow)**

***inline* shape([migraphx\_shape\_datatype\_t](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv425migraphx_shape_datatype_t) type)**

Construct a scalar shape.

***inline* shape([migraphx\_shape\_datatype\_t](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv425migraphx_shape_datatype_t) type, std::vector&lt;size\_t&gt; plengths)**

> Construct a shape with its type and lengths. The strides are
> automatically computed assumming a packed layout.

3.1.2 Argument
--------------

***struct* migraphx::argument : *public* migraphx::handle\_base&lt;&gt;**

Arguments to be passed to an migraphx arguments.

An argument represents a raw buffer of data with a shape.

**Public Functions**

***inline* argument()**

***inline* argument(migraphx\_argument \*p**, **borrow)**

***inline* argument(migraphx\_argument \*p**, **own)**

***inline* argument(*const* migraphx\_argument \*p)**

***inline* argument([shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) pshape, void \*pbuffer)**

***inline* [shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) get\_shape() *const***

***inline* char \*data() *const***

Public Static Functions

***static* *inline* [argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) generate([shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) ps, size\_t pseed = 0)**

Generate an argument using random data.

**Friends**

**inline** **friend** **friend** **bool** **operator==** **(const** **argument** **&px,** **const** **argument** **&py)**

**inline** **friend** **friend** **bool** **operator!=** **(const** **argument** **&px,** **const** **argument** **&py)**

3.1.3 Target
------------

***struct* migraphx::target : *public* migraphx::handle\_base&lt;&gt;**

A

target for compilation.

**Public Functions**

***inline* target()**

***inline* target(migraphx\_target \*p**, **own)**

***inline* target(migraphx\_target \*p**, **borrow)**

***inline* target(*const* char \*name)**

Construct a target from its name.

3.1.4 Program
-------------

***struct* migraphx::program\_parameter\_shapes : *public* migraphx::handle\_base&lt;&gt;**

Public Functions

***inline* program\_parameter\_shapes()**

***inline* program\_parameter\_shapes(migraphx\_program\_parameter\_shapes \*p**, **own)**

***inline* program\_parameter\_shapes(migraphx\_program\_parameter\_shapes \*p**, **borrow)**

***inline* size\_t size() *const***

***inline* [shape](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) *operator*\[\](*const* char \*pname) *const***

***inline* std::vector&lt;*const* char\*&gt; names() *const***

***struct* migraphx::program\_parameters : *public* migraphx::handle\_base&lt;&gt;**

A class to construct the inputs parameters for a program.

**Public Functions**

***inline* program\_parameters(migraphx\_program\_parameters \*p**, **own)**

***inline* program\_parameters(migraphx\_program\_parameters \*p**, **borrow)**

***inline* program\_parameters(migraphx\_program\_parameters \*p)**

***inline* program\_parameters()*inline* program\_parameters(std::initializer\_list&lt;std::pair&lt;std::string, [argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE)&gt;&gt; l)**

Construct the parameters from initializer\_list.

***inline* void add(*const* char \*pname, *const* [argument](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) &pargument) *const***

Add a new parameter.

***struct* migraphx\_compile\_options**

**Public Functions**

***template*&lt;*class* ...Ts&gt;\
*inline* migraphx\_compile\_options([Ts](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4IDpEN24migraphx_compile_options24migraphx_compile_optionsEDpRR2Ts)&&... xs)**

**Public Members**

**migraphx::compile\_options object**

***struct* migraphx::program : *public* migraphx::handle\_base&lt;&gt;**

A program represents the all computation graphs to be compiled and
executed.

**Public Functions**

***inline* program()**

***inline* program(migraphx\_program \*p**, **own)**

***inline* program(migraphx\_program \*p**, **borrow)**

***inline* void compile(*const* [target](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx6targetE) &ptarget, *const* compile\_options &poptions) *const***

Compile the program for a specific target to be ran on.

***inline* void compile(*const* [target](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx6targetE) &ptarget) *const***

Compile the program for a specific target to be ran on.

***inline* [program\_parameter\_shapes](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx24program_parameter_shapesE) get\_parameter\_shapes() *const***

Return the shapes for the input parameters.

***inline* shapes get\_output\_shapes() *const***

Get the shapes of all the outputs returned by this program.

***inline* arguments eval(*const* [program\_parameters](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx18program_parametersE) &pparams) *const***

Run the program using the inputs passed in.

***inline* void print() *const***

***inline* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) sort()**

***inline* module get\_main\_module()**

**Friends**

**inline** **friend** **friend** **bool** **operator==** **(const** **program** **&px,** **const** **program** **&py)**

**inline** **friend** **friend** **bool** **operator!=** **(const** **program** **&px,** **const** **program** **&py)**

3.1.5 Quantize
--------------

***struct* migraphx::quantize\_op\_names : *public* migraphx::handle\_base&lt;&gt;**

**Public Functions**

***inline* quantize\_op\_names()**

***inline* quantize\_op\_names(migraphx\_quantize\_op\_names \*p**, **own)**

***inline* void add(*const* std::string &name)**

***inline* void migraphx::quantize\_fp16(*const* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) &prog)**

Quantize program to use fp16.

***inline* void migraphx::quantize\_fp16(*const* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) &prog, *const* [quantize\_op\_names](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx17quantize_op_namesE) &names)**

Quantize program to use fp16.

***struct* migraphx::quantize\_int8\_options : *public* migraphx::handle\_base&lt;&gt;**

Options to be passed when quantizing for int8.

**Public Functions**

***inline* quantize\_int8\_options()**

***inline* quantize\_int8\_options(migraphx\_quantize\_int8\_options \*p**, **own)**

***inline* quantize\_int8\_options(migraphx\_quantize\_int8\_options \*p**, **borrow)**

***inline* void add\_op\_name(*const* std::string &name)**

Add an operator that should be quantized.

***inline* void add\_calibration\_data(*const* [program\_parameters](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx18program_parametersE) &pp)**

Add calibrartion data to be used for quantizing.

**Public Members**

**std::vector&lt;parameter\_map&gt; calibration = {}**

**std::vector&lt;std::string&gt; op\_names = {}**

***inline* void migraphx::quantize\_int8(*const* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) &prog, *const* [target](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx6targetE) &ptarget, *const* [quantize\_int8\_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx21quantize_int8_optionsE) &options)**

Quantize program to use int8.

3.1.6 parse\_onnx
-----------------

***struct* migraphx::onnx\_options : *public* migraphx::handle\_base&lt;&gt;**

Options for parsing onnx options.

**Public Functions**

***inline* onnx\_options()**

***inline* onnx\_options(migraphx\_onnx\_options \*p**, **own)**

***inline* void set\_input\_parameter\_shape(*const* std::string &name**, **std::vector&lt;std::size\_t&gt; dim)**

Make onnx parser treat an inputs with a certain dimensions.

***inline* void set\_default\_dim\_value(unsigned int value)**

When there is a dimension parameter, then use this default value.

***inline* void set\_default\_loop\_iterations(int64\_t value)**

Set default max iteration number for the loop operator.

***inline* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) migraphx::parse\_onnx(*const* char \*filename)**

Parse an onnx file into a migraphx program.

***inline* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) migraphx::parse\_onnx(*const* char \*filename, *const* migraphx::[onnx\_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx12onnx_optionsE) &options)**

Parse an onnx file into a migraphx program.

***inline* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) migraphx::parse\_onnx\_buffer(*const* std::string &buffer)**

Parse a buffer of memory as an onnx file.

***inline* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) migraphx::parse\_onnx\_buffer(*const* std::string &buffer, *const* migraphx::[onnx\_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx12onnx_optionsE) &options)**

Parse a buffer of memory as an onnx file.

***inline* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) migraphx::parse\_onnx\_buffer(*const* void \*data, size\_t size)**

Parse a buffer of memory as an onnx file.

***inline* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) migraphx::parse\_onnx\_buffer(*const* void \*data, size\_t size, *const* migraphx::[onnx\_options](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx12onnx_optionsE) &options)**

Parse a buffer of memory as an onnx file.

3.1.7 Load
----------

***struct* migraphx\_file\_options**

**Public Functions**

***template*&lt;*class* ...Ts&gt;\
*inline* migraphx\_file\_options([Ts](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4IDpEN21migraphx_file_options21migraphx_file_optionsEDpRR2Ts)&&... xs)**

**Public Members**

**migraphx::file\_options object**

Load a saved migraphx program from a file.

3.1.8 Save
----------

***inline* void migraphx::save(*const* [program](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) &p, *const* char \*filename)**

Save a program to a file.

4. MIGraphX Driver
==================

4.1 Description
===============

The MIGraphX driver is a tool that allows you to utilize many of the
core functions of MIGraphX without having to write your own program.

4.2 How to Use
==============

The MIGraphX driver is installed with MIGraphX and can be found
in */opt/rocm/bin/migraphx-driver*, or
in *AMDMIGraphX/build/bin/migraphx-driver* after building the source
code.

See below for a comprehensive list of commands and option arguments, as
well as some usage examples.

4.2.1 Commands
--------------

![](media/image2.png){width="6.5in" height="2.9291666666666667in"}

4.2.2 Options
-------------

![](media/image1.png){width="5.625in" height="3.2083333333333335in"}
--------------------------------------------------------------------

4.3 Defining different modules in detail
========================================

4.3.1 Read
----------

Loads and prints input graph.

**&lt;input file&gt;**

File to load

**--model \[resnet50|inceptionv3|alexnet\]**

Load model

--onnx

Load as onnx

--tf

Load as tensorflow

--migraphx

Load as MIGraphX

--migraphx-json

Load as MIGraphX JSON

--batch \[unsigned int\] (Default: 1)

Set batch size for model

--nhwc

Treat tensorflow format as nhwc

--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

--nchw

Treat tensorflow format as nchw

--trim, -t \[unsigned int\]

Trim instructions from the end (Default: 0)

--input-dim \[std::vector&lt;std::string&gt;\]

Dim of a parameter (format: “@name d1 d2 dn”)

--optimize, -O

Optimize when reading

--graphviz, -g

Print out a graphviz representation.

--brief

Make the output brief.

--cpp

Print out the program as cpp program.

--json

Print out program as json.

--text

Print out program in text format.

--binary

Print out program in binary format.

--output, -o \[std::string\]

Output to file.

4.3.2 compile
-------------

Compiles and prints input graph.

&lt;input file&gt;

File to load

--model \[resnet50|inceptionv3|alexnet\]

Load model

--onnx

Load as onnx

--tf

Load as tensorflow

--migraphx

Load as MIGraphX

--migraphx-json

Load as MIGraphX JSON

--batch \[unsigned int\] (Default: 1)

Set batch size for model

--nhwc

Treat tensorflow format as nhwc

--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

--nchw

Treat tensorflow format as nchw

--trim, -t \[unsigned int\]

Trim instructions from the end (Default: 0)

--input-dim \[std::vector&lt;std::string&gt;\]

Dim of a parameter (format: “@name d1 d2 dn”)

--optimize, -O

Optimize when reading

--graphviz, -g

Print out a graphviz representation.

--brief

Make the output brief.

--cpp

Print out the program as cpp program.

--json

Print out program as json.

--text

Print out program in text format.

--binary

Print out program in binary format.

--output, -o \[std::string\]

Output to file.

--fill0 \[std::vector&lt;std::string&gt;\]

Fill parameter with 0s

--fill1 \[std::vector&lt;std::string&gt;\]

Fill parameter with 1s

--gpu

Compile on the gpu

--cpu

Compile on the cpu

--ref

Compile on the reference implementation

--enable-offload-copy

Enable implicit offload copying

--disable-fast-math

Disable fast math optimization

--fp16

Quantize for fp16

--int8

Quantize for int8

4.3.3 Run 
----------

Loads and prints input graph.

&lt;input file&gt;

File to load

--model \[resnet50|inceptionv3|alexnet\]

Load model

--onnx

Load as onnx

--tf

Load as tensorflow

--migraphx

Load as MIGraphX

--migraphx-json

Load as MIGraphX JSON

--batch \[unsigned int\] (Default: 1)

Set batch size for model

--nhwc

Treat tensorflow format as nhwc

--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

--nchw

Treat tensorflow format as nchw

--trim, -t \[unsigned int\]

Trim instructions from the end (Default: 0)

--input-dim \[std::vector&lt;std::string&gt;\]

Dim of a parameter (format: “@name d1 d2 dn”)

--optimize, -O

Optimize when reading

--graphviz, -g

Print out a graphviz representation.

--brief

Make the output brief.

--cpp

Print out the program as cpp program.

--json

Print out program as json.

--text

Print out program in text format.

--binary

Print out program in binary format.

--output, -o \[std::string\]

Output to file.

--fill0 \[std::vector&lt;std::string&gt;\]

Fill parameter with 0s

--fill1 \[std::vector&lt;std::string&gt;\]

Fill parameter with 1s

--gpu

Compile on the gpu

--cpu

Compile on the cpu

--ref

Compile on the reference implementation

--enable-offload-copy

Enable implicit offload copying

--disable-fast-math

Disable fast math optimization

--fp16

Quantize for fp16

--int8

Quantize for int8

4.3.4 Perf 
-----------

Compiles and runs input graph then prints performance report.

&lt;input file&gt;

File to load

--model \[resnet50|inceptionv3|alexnet\]

Load model

--onnx

Load as onnx

--tf

Load as tensorflow

--migraphx

Load as MIGraphX

--migraphx-json

Load as MIGraphX JSON

--batch \[unsigned int\] (Default: 1)

Set batch size for model

--nhwc

Treat tensorflow format as nhwc

--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

--nchw

Treat tensorflow format as nchw

--trim, -t \[unsigned int\]

Trim instructions from the end (Default: 0)

--input-dim \[std::vector&lt;std::string&gt;\]

Dim of a parameter (format: “@name d1 d2 dn”)

--optimize, -O

Optimize when reading

--graphviz, -g

Print out a graphviz representation.

--brief

Make the output brief.

--cpp

Print out the program as cpp program.

--json

Print out program as json.

--text

Print out program in text format.

--binary

Print out program in binary format.

--output, -o \[std::string\]

Output to file.

--fill0 \[std::vector&lt;std::string&gt;\]

Fill parameter with 0s

--fill1 \[std::vector&lt;std::string&gt;\]

Fill parameter with 1s

--gpu

Compile on the gpu

--cpu

Compile on the cpu

--ref

Compile on the reference implementation

--enable-offload-copy

Enable implicit offload copying

--disable-fast-math

Disable fast math optimization

--fp16

Quantize for fp16

--int8

Quantize for int8

--iterations, -n \[unsigned int\]

Number of iterations to run for perf report (Default: 100)

4.3.5 Verify 
-------------

Runs reference and CPU or GPU implementations and checks outputs for
consistency.

&lt;input file&gt;

File to load

--model \[resnet50|inceptionv3|alexnet\]

Load model

--onnx

Load as onnx

--tf

Load as tensorflow

--migraphx

Load as MIGraphX

--migraphx-json

Load as MIGraphX JSON

--batch \[unsigned int\] (Default: 1)

Set batch size for model

--nhwc

Treat tensorflow format as nhwc

--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

--nchw

Treat tensorflow format as nchw

--trim, -t \[unsigned int\]

Trim instructions from the end (Default: 0)

--input-dim \[std::vector&lt;std::string&gt;\]

Dim of a parameter (format: “@name d1 d2 dn”)

--optimize, -O

Optimize when reading

--graphviz, -g

Print out a graphviz representation.

--brief

Make the output brief.

--cpp

Print out the program as cpp program.

--json

Print out program as json.

--text

Print out program in text format.

--binary

Print out program in binary format.

--output, -o \[std::string\]

Output to file.

--fill0 \[std::vector&lt;std::string&gt;\]

Fill parameter with 0s

--fill1 \[std::vector&lt;std::string&gt;\]

Fill parameter with 1s

--gpu

Compile on the gpu

--cpu

Compile on the cpu

--ref

Compile on the reference implementation

--enable-offload-copy

Enable implicit offload copying

--disable-fast-math

Disable fast math optimization

--fp16

Quantize for fp16

--int8

Quantize for int8

--tolerance \[double\]

Tolerance for errors (Default: 80)

-i, --per-instruction

Verify each instruction

-r, --reduce

Reduce program and verify

4.3.6 Roctx
-----------

Provides marker information for each operation, allowing MIGraphX to be
used
with [rocprof](https://rocmdocs.amd.com/en/latest/ROCm_Tools/ROCm-Tools.html) for
performance analysis. This allows user to get GPU-level kernel timing
information. An example command line combined with rocprof for tracing
purposes is given below:

/opt/rocm/bin/rocprof --hip-trace --roctx-trace --flush-rate 1ms
--timestamp on -d &lt;OUTPUT\_PATH&gt; --obj-tracking on
/opt/rocm/bin/migraphx-driver roctx &lt;ONNX\_FILE&gt;
&lt;MIGRAPHX\_OPTIONS&gt;

After **rocprof** is run, the output directory will contain trace
information for HIP, HCC and ROCTX in seperate **.txt** files. To
understand the interactions between API calls, it is recommended to
utilize **roctx.py** helper script as desribed
in dev/tools:rocTX section.

&lt;input file&gt;

File to load

--model \[resnet50|inceptionv3|alexnet\]

Load model

--onnx

Load as onnx

--tf

Load as tensorflow

--migraphx

Load as MIGraphX

--migraphx-json

Load as MIGraphX JSON

--batch \[unsigned int\] (Default: 1)

Set batch size for model

--nhwc

Treat tensorflow format as nhwc

--skip-unknown-operators

Skip unknown operators when parsing and continue to parse.

--nchw

Treat tensorflow format as nchw

--trim, -t \[unsigned int\]

Trim instructions from the end (Default: 0)

--input-dim \[std::vector&lt;std::string&gt;\]

Dim of a parameter (format: “@name d1 d2 dn”)

--optimize, -O

Optimize when reading

--graphviz, -g

Print out a graphviz representation.

--brief

Make the output brief.

--cpp

Print out the program as cpp program.

--json

Print out program as json.

--text

Print out program in text format.

--binary

Print out program in binary format.

--output, -o \[std::string\]

Output to file.

--fill0 \[std::vector&lt;std::string&gt;\]

Fill parameter with 0s

--fill1 \[std::vector&lt;std::string&gt;\]

Fill parameter with 1s

--gpu

Compile on the gpu

--cpu

Compile on the cpu

--ref

Compile on the reference implementation

--enable-offload-copy

Enable implicit offload copying

--disable-fast-math

Disable fast math optimization

--fp16

Quantize for fp16

--int8

Quantize for int8

5. Contributor Guide
====================

5.1 MIGraphX Fundamentals
=========================

MIGraphX provides an optimized execution engine for deep learning neural
networks. We will cover some simple operations in the MIGraphX framework
here. For a quick start guide to using MIGraphX, look in the example
directory: 

https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/tree/develop/examples/migraphx.

5.1.1 Location of the Examples
------------------------------

The ref\_dev\_examples.cpp can be found in the test directory (/test).
The executable file test\_ref\_dev\_examples based on this file will be
created in the bin/ of the build directory after
running make -j\$(nproc) test\_ref\_dev\_examples. The executable will
also be created when running make -j\$(nproc) check, alongside with all
the other tests. Directions for building MIGraphX from source can be
found in the main README file: 

<https://github.com/ROCmSoftwarePlatform/AMDMIGraphX#readme>.

5.1.2 Adding Two Literals
-------------------------

A program is a collection of modules, which are collections of
instructions to be executed when
calling [**eval**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4NK8migraphx7program4evalERK18program_parameters).
Each instruction has an associated **operation** which represents the
computation to be performed by the instruction.

We start with a snippet of the simple add\_two\_literals() function:

*// create the program and get a pointer to the main module*

migraphx::program p;

**auto**\* mm = p.get\_main\_module();

*// add two literals to the program*

**auto** one = mm-&gt;add\_literal(1);

**auto** two = mm-&gt;add\_literal(2);

*// make the add operation between the two literals and add it to the
program*

mm-&gt;add\_instruction(migraphx::make\_op("add"), one, two);

*// compile the program on the reference device*

p.compile(migraphx::ref::target{});

*// evaulate the program and retreive the result*

**auto** result = p.eval({}).back();

std::cout &lt;&lt; "add\_two\_literals: 1 + 2 = " &lt;&lt; result
&lt;&lt; "**\\n**";

We start by creating a simple migraphx::program object and then getting
a pointer to the main module of it. The program is a collection
of modules that start executing from the main module, so instructions
are added to the modules rather than directly onto the program object.
We then use the **add\_literal** function to add an instruction that
stores the literal number 1 while returning an **instruction\_ref**. The
returned **instruction\_ref** can be used in another instruction as an
input. We use the same **add\_literal** function to add a 2 to the
program. After creating the literals, we then create the instruction to
add the numbers together. This is done by using
the **add\_instruction** function with the "add" **operation** created
by **make\_op** along with the
previous **add\_literal** **instruction\_ref** for the input arguments
of the instruction. Finally, we can run
this [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) by
compiling it for the reference target (CPU) and then running it
with [**eval**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4NK8migraphx7program4evalERK18program_parameters) The
result is then retreived and printed to the console.

We can compile the program for the GPU as well, but the file will have
to be moved to the test/gpu/ directory and the correct target must be
included:

\#include *&lt;migraphx/gpu/target.hpp&gt;*

5.1.3 Using Parameters
----------------------

The previous program will always produce the same value of
adding 1 and 2. In the next program we want to pass an input to a
program and compute a value based on the input. We can modify the
program to take an input parameter x, as seen in
the add\_parameter() function:

migraphx::program p;

**auto**\* mm = p.get\_main\_module();

migraphx::shape s{migraphx::shape::int32\_type, {1}};

*// add a "x" parameter with the shape s*

**auto** x = mm-&gt;add\_parameter("x", s);

**auto** two = mm-&gt;add\_literal(2);

*// add the "add" instruction between the "x" parameter and "two" to the
module*

mm-&gt;add\_instruction(migraphx::make\_op("add"), x, two);

p.compile(migraphx::ref::target{});

This adds a parameter of type int32, and compiles it for the CPU. To run
the program, we need to pass the parameter as a parameter\_map when we
call [**eval**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4NK8migraphx7program4evalERK18program_parameters).
We create the parameter\_map by setting the x key to
an [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) object
with an int data type:

*// create a parameter\_map object for passing a value to the "x"
parameter*

std::vector&lt;int&gt; data = {4};

migraphx::parameter\_map params;

params\["x"\] = migraphx::argument(s, data.data());

**auto** result = p.eval(params).back();

std::cout &lt;&lt; "add\_parameters: 4 + 2 = " &lt;&lt; result &lt;&lt;
"**\\n**";

EXPECT(result.at&lt;int&gt;() == 6);

5.1.4 Handling Tensor Data
--------------------------

In the previous examples we have only been dealing with scalars, but
the [**shape**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx5shapeE) class
can describe multi-dimensional tensors. For example, we can compute a
simple convolution:

migraphx::program p;

**auto**\* mm = p.get\_main\_module();

*// create shape objects for the input tensor and weights*

migraphx::shape input\_shape{migraphx::shape::float\_type, {2, 3, 4,
4}};

migraphx::shape weights\_shape{migraphx::shape::float\_type, {3, 3, 3,
3}};

*// create the parameters and add the "convolution" operation to the
module*

**auto** input = mm-&gt;add\_parameter("X", input\_shape);

**auto** weights = mm-&gt;add\_parameter("W", weights\_shape);

mm-&gt;add\_instruction(migraphx::make\_op("convolution", {{"padding",
{1, 1}}, {"stride", {2, 2}}}), input, weights);

Here we create two parameters for both the input and weights. In the
previous examples, we created simple literals, however, most programs
will take data from allocated buffers (usually on the GPU). In this
case, we can
create [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) objects
directly from the pointers to the buffers:

*// Compile the program*

p.compile(migraphx::ref::target{});

*// Allocated buffers by the user*

std::vector&lt;float&gt; a = ...;

std::vector&lt;float&gt; c = ...;

*// Solution vector*

std::vector&lt;float&gt; sol = ...;

*// Create the arguments in a parameter\_map*

migraphx::parameter\_map params;

params\["X"\] = migraphx::argument(input\_shape, a.data());

params\["W"\] = migraphx::argument(weights\_shape, c.data());

*// Evaluate and confirm the result*

**auto** result = p.eval(params).back();

std::vector&lt;float&gt; results\_vector(64);

result.visit(\[&\](**auto** output) {
results\_vector.assign(output.begin(), output.end()); });

EXPECT(migraphx::verify\_range(results\_vector, sol));

An [**argument**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx8argumentE) can
handle memory buffers from either the GPU or the CPU. By default when
running
the [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE),
buffers are allocated on the corresponding target. When compiling for
the CPU, the buffers by default will be allocated on the CPU. When
compiling for the GPU, the buffers by default will be allocated on the
GPU. With the option offloaf\_copy=true set while compiling for the GPU,
the buffers will be located on the CPU.

5.1.5 Importing From ONNX
-------------------------

A [**program**](https://rocmsoftwareplatform.github.io/AMDMIGraphX/doc/html/reference/cpp.html#_CPPv4N8migraphx7programE) can
be built directly from an onnx file using the MIGraphX ONNX parser. This
makes it easier to use neural networks directly from other frameworks.
In this case, there is an parse\_onnx function:

program p = migraphx::parse\_onnx("model.onnx");

p.compile(migraphx::gpu::target{});
