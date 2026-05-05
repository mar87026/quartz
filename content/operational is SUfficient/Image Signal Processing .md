# Image Signal Processing

1. ISP Tuning and Algorithm Design Are Two Different Disciplines
2. Both Can End Up Amplifying Image Quality
3. Module Ordering in Algorithm Design Should Be Cost-Driven, While ISP Debugging Must Follow Signal Dependency

## This section serves as the main ISP entry point.

Outlining the core problems handled across these two engineering domains and the image quality standards they are expected to meet.

[Problem Note : Sensor](Image%20Signal%20Processing/Problem%20Note%20Sensor%20.md)

[Problem Note : Lens](Image%20Signal%20Processing/Problem%20Note%20Lens%20.md)

| **Spatial Frequency Response**  |
| --- |
| Low: represent large, broad changes, like the overall shape of an object or a smooth gradient. |
| High:represent fine details, such as edge of object, textures, or very thin lines. |

| Slanted-edge Method |
| --- |
| 計算MTF，用斜邊法可一張圖產生一個MTF曲線
多個亮度可以拍攝能計算HDR db值的slope based |

| Noun/Unit |  |
| --- | --- |
| frame rate/fps | 幀率 |
|  |  |

The algorithm section focuses on documenting candidate solution strategies together with their benefits, limitations, and computational trade-offs.

[ISP Algorthn](Image%20Signal%20Processing/ISP%20Algorthn%20.md)

The tuning and debugging section records practical adjustment methods, possible corrective actions, and the downstream impact they may introduce throughout the ISP pipeline.

[ISP Tuning](Image%20Signal%20Processing/ISP%20Tuning%20.md)