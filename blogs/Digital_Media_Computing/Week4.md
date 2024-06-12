# Week 4 - Digital Image Processing


- Full-color processing
- Pseudo-color processing - artificial color

## Color Fundamentals

- long wave length - red color
- short wave length - blue color

Color we see from a object is the color that reflected from the object.

Chromatic light source is described with three basic quantities.
- Radiance
- Luminance
- Brightness

Human eyes
- Rod - sensitive with light
- Cones - sensitive with color

Color models
- RGB
  - Saturation of red, green and blue
  - Safe RGB Colors
- CMYK
  - Cyan = no red
  - Yellow = no blue
- HSV
  - Used to describe color
  - Hue
  - Saturation
  - Brightness

## Color Image Processing

$$\text{Dynamic Range} = \frac{\text{Max Luminance}}{\text{Min Luminance}}$$

### Highq Dynamic Range Imaging

#### Creat
- Hardware
- Software
  - capture vary exposure and combine them

#### ImageRegistration and Alignment


#### Ghost Removal

Remove moving objects.

Calculate the  weighted variance to detect moving objects.

#### Lens Flare Removal

#### Storage

### Tone Mapping
Map scene luminances to display luminances.

#### Global Operator

$$L_m(x,y) = \frac{a}{\overline{L}_w}L_w(x,y)$$
$$L_d(x,y)=\frac{L_m(x,y)}{1+L_m(x,y)}$$ 

#### Frequency Domain

$$\text{image} = \text{illuminance}*\text{reflectance}$$