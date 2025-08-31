
# ImagetoImage with Stable Diffusion

This project demonstrates **imagetoimage generation** using **Stable Diffusion v1.5** via HuggingFace **Diffusers**.
It allows transforming an input image into a new one guided by a **text prompt**, with control over **strength** and **guidance scale**.

The project also includes a **Gradio web interface** for interactive experimentation.



## 📌 Features

* Uses **Stable Diffusion v1.5** (`runwayml/stablediffusionv15`).
* Accepts an input image and transforms it based on a **text prompt**.
* Adjustable parameters:

  * **strength** → controls how much the generated image diverges from the original (0–1).
  * **guidance\_scale** → controls prompt adherence (higher values = closer to prompt).
* Gradiobased UI for easy experimentation.
* Script also includes a **texttoimage** example (astronaut riding a horse on Mars 🐴🚀).



## 🛠 Installation

Install dependencies:

```bash
pip install diffusers transformers accelerate gradio
```



## 🚀 Usage

### 1. Run the Gradio App

Launch the interactive imagetoimage tool:

```bash
python image2image_stable_diffusion.py
```

This starts a Gradio web interface where you can:

1. Upload an input image.
2. Enter a text prompt.
3. Adjust **strength** and **guidance\_scale** with sliders.
4. Generate a new image.

### 2. Example (TexttoImage)

The script also includes a standalone texttoimage example:

```python
from diffusers import StableDiffusionPipeline
import torch

model_id = "runwayml/stablediffusionv15"
pipe = StableDiffusionPipeline.from_pretrained(model_id, torch_dtype=torch.float16).to("cuda")

prompt = "a photo of an astronaut riding a horse on mars"
image = pipe(prompt).images[0]
image.save("astronaut_rides_horse.png")
```

This saves the generated image as `astronaut_rides_horse.png`.



## 🎛 Parameters

* **strength (0–1):**

  * Low = keeps original image features.
  * High = closer to text prompt, more deviation from original.
* **guidance\_scale (1–30):**

  * Low = more creativity, less prompt control.
  * High = closer to prompt, less randomness.



## 🔮 Future Enhancements

* Add support for multiple SD models (e.g., SDXL).
* Enable batch image processing.
* Add support for saving multiple generated variations.



