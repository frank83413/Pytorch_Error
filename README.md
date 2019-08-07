# Pytorch_Error

20190807 pytorch version 1.1.0
```
RuntimeError:
        An attempt has been made to start a new process before the
        current process has finished its bootstrapping phase.

        This probably means that you are not using fork to start your
        child processes and you have forgotten to use the proper idiom
        in the main module:

            if __name__ == '__main__':
                freeze_support()
                ...

        The "freeze_support()" line can be omitted if the program
        is not going to be frozen to produce an executable.
```
try
```
def run():
  ...
	freeze_support()
	...

if __name__ == '__main__':
	run()
```
----------

RuntimeError: expected backend CUDA and dtype Float but got backend CUDA and dtype Long

Change the dtype of the torch.Tensor
```
tensor = torch.randn(3, 5)
tensor = tensor.float()
print(tensor.dtype)
```
----------

IndexError: invalid index of a 0-dim tensor. Use tensor.item() to convert a 0-dim tensor to a Python number

The index of 0-dim tensor is invalid in new version of torch

Change

`loss_total = loss_a.data[0] + loss_b.data[0] + loss_c.data[0]`

To

`loss_total = loss_a.data + loss_b.data + loss_c.data`
