# FHOG Python Wrapper

A python wrapper for the fhog function of PDollar Toolbox.
This function is widely used in visual tracking algorithms(e.g fDSST, ECO) to extract HOG feature.

#### Install
`python setup.py build_ext --inplace && python setup.py install`

#### Usage
```python
import fhog
def FHOG(imgPatch, binSize=8, nOrients=9, clip=.2, softBin=-1, useHog=2):
    nChns = nOrients if useHog == 0 else (nOrients * 4 if useHog == 1 else nOrients*3+5)
    h, w = imgPatch.shape[:2]
    M = np.zeros((h, w), dtype='float32')
    O = np.zeros((h, w), dtype='float32')
    H = np.zeros([img.shape[0] // binSize, imgPatch.shape[1] // binSize, nChns], dtype='float32')
    fhog.gradientMag(img.astype(np.float32), M, O, 0, 1)
    fhog.gradientHist(M, O, H, binSize, nOrients, softBin, useHog, clip)
    return H
```

#### References
- Adapted from: https://github.com/lawpdas/fhog-python
- [pdollar/toolbox](https://github.com/pdollar/toolbox)

