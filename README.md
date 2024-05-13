# Relighting-pettaha


Relighting-pettaha is a project to manipulate the illumination of images.

The name "Relighting-pettaha" stands for **"Imposing Consistent Light"**.

Currently, we release two types of models: text-conditioned relighting model and background-conditioned model. Both types take foreground images as inputs.

# Get Started

Below script will run the text-conditioned relighting model:

    git clone https://github.com/Metacolombo/Relighting-pettaha.git
    Relighting-pettaha
    conda create -n iclight python=3.10
    conda activate iclight
    pip install torch torchvision --index-url https://download.pytorch.org/whl/cu121
    pip install -r requirements.txt
    python gradio_demo.py

Or, to use background-conditioned demo:

    python gradio_demo_bg.py

Model downloading is automatic.




# Imposing Consistent Light

In HDR space, illumination has a property that all light transports are independent. 

As a result, the blending of appearances of different light sources is equivalent to the appearance with mixed light sources:

Using the above light stage as an example, the two images from the "appearance mixture" and "light source mixture" are consistent (mathematically equivalent in HDR space, ideally).

We imposed such consistency (using MLPs in latent space) when training the relighting models.

As a result, the model is able to produce highly consistent relight - **so** consistent that different relightings can even be merged as normal maps! Despite the fact that the models are latent diffusion.



From left to right are inputs, model outputs relighting, devided shadow image, and merged normal maps. Note that the model is not trained with any normal map data. This normal estimation comes from the consistency of relighting.






# Model Notes

* **Relighting-pettaha_sd15_fc.safetensors** - The default relighting model, conditioned on text and foreground. You can use initial latent to influence the relighting.

* **Relighting-pettaha_sd15_fcon.safetensors** - Same as "Relighting-pettaha_sd15_fc.safetensors" but trained with offset noise. Note that the default "Relighting-pettaha_sd15_fc.safetensors" outperform this model slightly in a user study. And this is the reason why the default model is the model without offset noise.

* **Relighting-pettaha_sd15_fbc.safetensors** - Relighting model conditioned with text, foreground, and background.

  www.pettahai.com | seja menath de silva 2024


