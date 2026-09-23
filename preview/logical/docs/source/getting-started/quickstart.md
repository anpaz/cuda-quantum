# Quick start

Start with a CUDA-Q kernel, or use `cudaq.logical` to write a logical program
directly without a kernel. CUDA-Q Logical is included with `cudaq` and can also
be installed separately as `cudaq-logical`. The examples below create the same
Bell pair both ways and report its logical resources.

## Use a CUDA-Q kernel

Install CUDA-Q, which includes CUDA-Q Logical:

```bash
pip install cudaq
```

The [kernel example][kernel-example] creates
a Bell pair, selects the logical estimator, and reports its resource counts:

```{literalinclude} ../../../examples/00_logical_resource_estimate.py
:language: python
:start-at: import cudaq
:caption: examples/00_logical_resource_estimate.py
```

To run this example, copy the code into `bell_kernel.py` and run
`python3 bell_kernel.py`. The example is also available in a checked-out
repository; from its root, run
`python3 preview/logical/examples/00_logical_resource_estimate.py`.

The program prints:

```text
Logical Bell-pair resources:
  peak logical qubits: 2
  Hadamard actions: 1
  controlled-X actions: 1
```

## Write a standalone logical program

You can use CUDA-Q Logical without writing a CUDA-Q kernel. To install it
separately, run:

```bash
pip install "cudaq-logical[cu13]"
```

Use `[cu12]` instead if you have CUDA 12 installed. Keep one of these extras:
the bare `cudaq-logical` package omits required dependencies. If you installed
`cudaq` above, `cudaq.logical` is already available; no second install is
needed.

The [standalone example][standalone-example]
defines the same Bell pair directly and estimates its logical resources:

```{literalinclude} ../../../examples/standalone/00_logical_program.py
:language: python
:start-at: import cudaq.logical as cql
:caption: examples/standalone/00_logical_program.py
```

To run this example, copy the code into `bell_logical.py` and run
`python3 bell_logical.py`. The example is also available in a checked-out
repository; from its root, run
`python3 preview/logical/examples/standalone/00_logical_program.py`.

The program prints:

```text
Portable Bell program: 2 logical qubits
```

These are logical counts; neither example chooses a QEC code or a device. For
placement, QEC, and physical estimates, continue with
[The logical programming stack](cudaq-logical-in-practice.md) or browse the
[examples](../use-cases/examples/index.md).

[kernel-example]:
https://github.com/NVIDIA/cuda-quantum/blob/main/preview/logical/examples/00_logical_resource_estimate.py

[standalone-example]:
https://github.com/NVIDIA/cuda-quantum/blob/main/preview/logical/examples/standalone/00_logical_program.py
