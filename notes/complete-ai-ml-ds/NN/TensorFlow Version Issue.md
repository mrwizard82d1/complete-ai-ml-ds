The code that Daniel wrote in the next video failed to create a model in my original environment.

I had created a conda environment with the latest version of TensorFlow, 2.18.0. Based on [this issue in Daniel's GitHub repository](https://github.com/mrdbourke/zero-to-mastery-ml/issues/100), I believe the issue is known.

To repair it, as [this issue in Daniel's GitHub repository](https://github.com/mrdbourke/zero-to-mastery-ml/issues/100) describes, I also had to:
- Downgrade my version of Python to 2.10
- Downgrade my version of `numpy` to 1.26
- Change my `conda` environment file, `tf-metal-arm64.yaml`, to reflect these pinned packages
- Rebuild the `conda` environment, `dog-vision`
- Re-open my PyCharm project which recognized the new environment and updated its skeletons (took a bit longer for the `numpy`downgrade that I expected)
- Re-ran all cells in my notebook in PyCharm
- Needed to make a minor correction to the optimizer
	- "WARNING:absl:At this time, the v2.11+ optimizer `tf.keras.optimizers.Adam` runs slowly on M1/M2 Macs, please use the legacy Keras optimizer instead, located at `tf.keras.optimizers.legacy.Adam`."