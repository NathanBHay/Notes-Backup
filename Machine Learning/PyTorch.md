PyTorch is a [[Python]], [[Machine Learning|machine learning]] library which functions on the use of tensors, a mathematical generalisation of [[Linear Algebra|matrices]] that run on the GPU, and deep learning components to build efficient [[Neural Networks|neural networks]].

# Tensor Operations
Tensor's have a variety of operations that allow for fast creation of the data structure. To create a tensor you can convert a tuple, or array data structure. For automatic creation use the `torch.tensor(...)` operation, or for type security use `torch.from_numpy()`.

Tensors can be created from a shape vector. This vector is then turned into an array of that shape with the properties of the function. These include:
- `rand(shape)` which randomly distributes the elements.
- `ones(shape)` which puts all elements as 1.
- `zeros(shape)` which puts all elements as 0.

Tensors have attributes that can be accessed through a member call. These include `shape`, `dtype`, and `device`. Device being used to find whether the tensor is on the CPU or GPU.

Tensors can be put onto Nvidia cuda cores through the `tensor.to(...)` operation.

Tensors have a variety of common operations found on matrices:
- **Matrix multiplication** can be called with `tensor.matmul(tensor.T)` or `tensor @ tensor.T`.
- **Concatenate** can be called with `torch.cat(...)`.
- **In place operations** are usually called with `tensor.add_(...)`.

# Dataset Loading
PyTorch has two common primitives used for loading datasets, those are `torch.utils.data.DataLoader` and `torch.utils.data.Dataset`. **Dataset** stores the samples and their corresponding data. **Data loader** wraps an iterable around the dataset to enable easy access to samples. Additionally there are common datasets provided in the dataset module.

To implement a custom dataset with the inherited `Datatset` class three functions must be implemented, those are `__init__`, `__len__`, and `__getitem__`. The get item operation is interesting as it takes a given index as an argument.

After a dataset has been loaded into the Dataset class it can be iterated through with a call to the data loader function. This is done through:
```
dataloader = Dataloader(training_data, batchsize=..., shuffle=True)
```
Given cases where shuffle is true the dataset shuffles after it has been fully iterated through.

# Neural Networks
Neural networks can be built by inheriting from the class `nn.Module`. This class has the following methods that need to be initialized `__init__`, and a `forward(x)` function.
