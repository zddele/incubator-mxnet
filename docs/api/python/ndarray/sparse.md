# Sparse NDArray API

```eval_rst
.. currentmodule:: mxnet.ndarray.sparse
```

## Overview

This document lists the routines of the *n*-dimensional sparse array package:

```eval_rst
.. autosummary::
    :nosignatures:

    mxnet.ndarray.sparse
```

The `CSRNDArray` and `RowSparseNDArray` API, defined in the `ndarray.sparse` package, provides
imperative sparse tensor operations on CPU.

An `CSRNDArray` inherits from `NDArray`, and represents a two-dimensional, fixed-size array in compressed sparse row format.

```python
>>> x = mx.nd.array([[1, 0], [0, 0], [2, 3]])
>>> csr = x.tostype('csr')
>>> type(csr)
<class 'mxnet.ndarray.sparse.CSRNDArray'>
>>> csr.shape
(3, 2)
>>> csr.data.asnumpy()
array([ 1.  2.  3.], dtype=float32)
>>> csr.indices.asnumpy()
array([0, 0, 1])
>>> csr.indptr.asnumpy()
array([0, 1, 1, 3])
>>> csr.stype
'csr'
```

An `RowSparseNDArray` inherits from `NDArray`, and represents a multi-dimensional, fixed-size array in row sparse format.

```python
>>> x = mx.nd.array([[1, 0], [0, 0], [2, 3]])
>>> row_sparse = x.tostype('row_sparse')
>>> type(row_sparse)
<class 'mxnet.ndarray.sparse.RowSparseNDArray'>
>>> row_sparse.data.asnumpy()
array([[ 1.  0.],
       [ 2.  3.]], dtype=float32)
>>> row_sparse.indices.asnumpy()
array([0, 2])
>>> row_sparse.stype
'row_sparse'
```

```eval_rst

.. note:: ``mxnet.ndarray.sparse`` is similar to ``mxnet.ndarray`` in some aspects. But the differences are not negligible. For instance:

   - Only a subset of operators in ``mxnet.ndarray`` have specialized implementations in ``mxnet.ndarray.sparse``.
     Operators such as reduction and broadcasting do not have sparse implementations yet.
   - The storage types (``stype``) of sparse operators' outputs depend on the storage types of inputs.
     By default the operators not available in ``mxnet.ndarray.sparse`` infer "default" (dense) storage type for outputs.
     Please refer to the API reference section for further details on specific operators.
   - GPU support for ``mxnet.ndarray.sparse`` is experimental.

```

In the rest of this document, we first overview the methods provided by the
`ndarray.sparse.CSRNDArray` class and the `ndarray.sparse.RowSparseNDArray` class,
and then list other routines provided by the `ndarray.sparse` package.

The `ndarray.sparse` package provides several classes:

```eval_rst
.. autosummary::
    :nosignatures:

    CSRNDArray
    RowSparseNDArray
```

We summarize the interface for each class in the following sections.

## The `CSRNDArray` class

### Array attributes

```eval_rst
.. autosummary::
    :nosignatures:

    CSRNDArray.shape
    CSRNDArray.size
    CSRNDArray.context
    CSRNDArray.dtype
    CSRNDArray.stype
    CSRNDArray.data
    CSRNDArray.indices
    CSRNDArray.indptr
```

### Array conversion

```eval_rst
.. autosummary::
    :nosignatures:

    CSRNDArray.copy
    CSRNDArray.copyto
    CSRNDArray.as_in_context
    CSRNDArray.asnumpy
    CSRNDArray.asscalar
    CSRNDArray.astype
    CSRNDArray.tostype
```

### Array creation

```eval_rst
.. autosummary::
    :nosignatures:

    CSRNDArray.zeros_like
```

### Indexing

```eval_rst
.. autosummary::
    :nosignatures:

    CSRNDArray.__getitem__
    CSRNDArray.__setitem__
    CSRNDArray.slice
```

### Lazy evaluation

```eval_rst
.. autosummary::
    :nosignatures:

    CSRNDArray.wait_to_read
```

## The `RowSparseNDArray` class

### Array attributes

```eval_rst
.. autosummary::
    :nosignatures:

    RowSparseNDArray.shape
    RowSparseNDArray.size
    RowSparseNDArray.context
    RowSparseNDArray.dtype
    RowSparseNDArray.stype
    RowSparseNDArray.data
    RowSparseNDArray.indices
```

### Array conversion

```eval_rst
.. autosummary::
    :nosignatures:

    RowSparseNDArray.copy
    RowSparseNDArray.copyto
    RowSparseNDArray.as_in_context
    RowSparseNDArray.asnumpy
    RowSparseNDArray.asscalar
    RowSparseNDArray.astype
    RowSparseNDArray.tostype
```

### Array creation

```eval_rst
.. autosummary::
    :nosignatures:

    RowSparseNDArray.zeros_like
```

### Indexing

```eval_rst
.. autosummary::
    :nosignatures:

    RowSparseNDArray.__getitem__
    RowSparseNDArray.__setitem__
```

### Lazy evaluation

```eval_rst
.. autosummary::
    :nosignatures:

    RowSparseNDArray.wait_to_read
```

## Array creation routines

```eval_rst
.. autosummary::
    :nosignatures:

    array
    empty
    zeros
    zeros_like
    csr_matrix
    row_sparse_array
```

## Array manipulation routines

### Changing array storage type

```eval_rst
.. autosummary::
    :nosignatures:

    cast_storage
```

### Indexing routines

```eval_rst
.. autosummary::
    :nosignatures:

    slice
    retain
```

## Mathematical functions

### Arithmetic operations

```eval_rst
.. autosummary::
    :nosignatures:

    elemwise_add
    dot
    add_n
```

## API Reference

<script type="text/javascript" src='../../../_static/js/auto_module_index.js'></script>

```eval_rst

.. autoclass:: mxnet.ndarray.sparse.CSRNDArray
    :members: shape, size, context, dtype, stype, data, indices, indptr, copy, copyto, as_in_context, asnumpy, asscalar, astype, tostype, slice, wait_to_read, zeros_like, __getitem__, __setitem__

.. autoclass:: mxnet.ndarray.sparse.RowSparseNDArray
    :members: shape, size, context, dtype, stype, data, indices, copy, copyto, as_in_context, asnumpy, asscalar, astype, tostype, wait_to_read, zeros_like, __getitem__, __setitem__

.. automodule:: mxnet.ndarray.sparse
    :members:
    :special-members:
    :exclude-members: BaseSparseNDArray, RowSparseNDArray, CSRNDArray

.. automodule:: mxnet.ndarray.sparse
    :members: array, zeros, empty

```

<script>auto_index("api-reference");</script>
