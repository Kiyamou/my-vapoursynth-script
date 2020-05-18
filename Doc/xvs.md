# xvs

### `mwcfix()`

Chroma restoration, containing  upscale by eedi2 / nnedi3 and downscale by bicubic (b=0, c=0.5), contra sharpening, line thinning / awarp and post-processing (repair).

```python
mwcfix(clip, kernel=1, restore=5, a=2, grad=2, warp=6, thresh=96, blur=3, repair=1, cs_h=0, cs_v=0)
```

* ***kernel***: Select edge directive interpolation method
  * kernel <= 0: none
  * kernel = 1: use znedi3
  * kernel >= 2: use eedi2

* ***restore***: Contra sharpening (by KNLMeansCL and RemoveGrain)
  * restore <= 0: no contra sharpening
  * restore > 0: same as `h` in `knlm.KNLMeansCL`

* ***a***: For contra sharpening
  * same as `a` in `knlm.KNLMeansCL`

* ***grad***: For contra sharpening
  * the number of RemoveGrain for contra sharpening 

* ***warp***: For line thinning / awarp
  * warp <= 0: no line thinning
  * warp > 0: same as `depth` in `warp.AWarp`

* ***thresh***: For line thinning / awarp
  * same as `thresh` in `warp.ASobel`

* ***blur***: For line thinning / awarp
  * same as `blur` in `warp.ABlur`

* ***repair***: For repair
  * warp <= 0: no repair
  * warp > 0: same as `mode` in `rgvs.repair`

* ***cs_h***: chroma shift on horizontal

* ***cs_v***: chroma shift on vertical
