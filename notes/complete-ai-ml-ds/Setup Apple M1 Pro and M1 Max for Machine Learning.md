See [this page by Daniel Bourke](https://www.mrdbourke.com/setup-apple-m1-pro-and-m1-max-for-machine-learning-and-data-science/)

From video
- Install `brew`
- Add `brew` to your path
- Download Miniforge3
	- Conda installer for macOS arm64 chips
	- Don't know if this is still necessary
- Install Miniforge3 into home directory
	- `chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh`
	- `sh ~/Downloads/Miniforge3-MaxOSX-arm64.sh`
	- `source ~/miniforge3/bin/activate`
- Re-open terminal
- Create directory to setup TensorFlow environment
	- `mkdir tensorflow-test`
	- `cd tensorflow-test`

I did not finish watching Daniel's video. I was able to install an envirnoment using the instructions in this [accepted answer](https://stackoverflow.com/questions/72964800/what-is-the-proper-way-to-install-tensorflow-on-apple-m1-in-2022)
