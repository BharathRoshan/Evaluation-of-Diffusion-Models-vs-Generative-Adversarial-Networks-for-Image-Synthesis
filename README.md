# Comparing Diffusion Models and GANs for Image Synthesis

Research project exploring image generation with diffusion and GAN/VQ-VAE approaches on **Oxford Flowers 102** and **CIFAR-10**. The notebooks are the primary research artifacts; this repository now includes a reproducibility guide and a place to record benchmark results.

## Research questions

- How do the selected generative approaches differ in sample quality and training behavior?
- How do dataset choice and image resolution affect the comparison?
- What trade-offs appear between sample fidelity, diversity, compute, and training stability?

## Notebooks

| Notebook | Focus |
|---|---|
| `Diffusion_Model_Oxford.ipynb` | Diffusion-model experiment on Oxford Flowers 102 |
| `StyleGAN2_Oxford_Flower.ipynb` | StyleGAN2 experiment on Oxford Flowers 102 |
| `VQ_VAE_Oxford_Flower.ipynb` | VQ-VAE experiment on Oxford Flowers 102 |
| `VQ_VAE_CIFAR.ipynb` | VQ-VAE experiment on CIFAR-10 |

Open a notebook in GitHub or use the **Open in Colab** badge where available. The original notebooks include Colab-oriented setup and may need dependency/version updates to run in a current environment.

## Reproducing an experiment

1. Choose a notebook and record the dataset, image size, model configuration, random seed, and hardware.
2. Run the notebook from top to bottom in a fresh runtime.
3. Save generated samples and training curves with the configuration used to create them.
4. Record the number of training steps, elapsed time, peak memory if available, and evaluation metrics.
5. Repeat runs where practical. Report the mean and spread rather than relying on one run.
6. Keep comparisons fair: use the same dataset split and evaluation preprocessing, and document differences in compute budget.

## Evaluation

For image generation, report more than visual examples:

- **FID** for distribution-level image quality (state the implementation and feature extractor).
- **Precision and recall for generative models** when available, to distinguish fidelity from diversity.
- Training steps, elapsed time, hardware, and sample count.
- A grid of generated samples and a brief discussion of visible failure modes.

Metrics are sensitive to sample count, preprocessing, and implementation. Compare scores only when these choices are aligned. Do not compare results across datasets as if they were the same benchmark.

## Results table

Use `results/benchmark_template.csv` to record your own runs. The template is intentionally blank: fill it only with measurements produced by your experiments. Include a commit or configuration identifier so a result can be traced back to the code that produced it.

## Environment notes

The notebooks were developed for a hosted notebook environment and install dependencies inline. A starting dependency list is provided in `requirements.txt`, but it is not a lockfile and does not guarantee compatibility with every notebook. For reproducibility, record the Python, PyTorch, CUDA, torchvision, and metric-library versions that actually worked.

## Current limitations

- These are research notebooks rather than a packaged training library.
- Runtime, memory, and results depend on the selected runtime and configuration.
- Some notebook cells may use legacy APIs or hosted-environment paths.
- No benchmark claims are made by this README; populate the results table after re-running and validating the experiments.

## Suggested next steps

- Consolidate repeated model and metric code into reusable modules.
- Add a single configuration file per experiment and seed control.
- Save generated samples and metrics to a predictable `outputs/` directory.
- Add a small smoke-test mode before starting a full training run.
