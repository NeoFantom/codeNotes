# Python coding notes

## Numpy

1. Sava an object (such as a `dict`) using `np.save` results in a "0-dimension array', which contains only one object, and should be accessed by:
   ```python
   np.save(path, obj)
   another = np.load(path)
   # either
   another = another[()]
   # or equivly
   another = another.item()
   ```
