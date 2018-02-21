# Machine learning and fMRI

NiLearn and NiStats

Installation: (On Win 10 x64) Most guides are written for Unix based OSes.

Download and install 64bit Anaconda for Python3.
Install it not for every user, only for yourself, especially if you are not using an account with admin privileges. (You shouldn't)
DO not add it to PATH, use Anaconda Prompt.

Once the installation is complete, start `anaconda prompt`. This will be our terminal. 
Go to the directory where you store your projects. For me it is `~\OneDrive\Documents\workspace` . 
(Linux and Mac users will use `/` instead of `\ ` ).  
Create a new folder/directory there. Use the GUI or the terminal `mkdir neuroimaging`. 
If you already have projcts that you intend to use with Nilearn, then this step is optional. I am creating it as a space to store the files I will generate as I learn to use these packages.

If you use pycharm then let pycharm handle all this, instead of the terminal. While the environment is
active in a terminal window, it is in accessible to other program, which means pycharm will either create 
inconvenient scenarios- the interpreter might become inacessible to pycharm or pycharm will end up
creating a copy of the env in the env entries. 
 
Create a new virtual environment using conda.
	
	> conda create -n neuroimaging  
Press `y` to confirm and `ENTER`.  

Activate the virtual environment.
	
	> activate neuroimaging

To see the list of packages already installed in the new environment, run 

	(neuroimaging) > conda list
	  
if `pip` is not installed, install it.

	(neuroimaging) > conda install pip

Choose`y` when prompted if you are sure.  

You can use pip to install nilearn and nistats, as specified in the official documentation, or use conda and install from the conda-forge channel.

I use pip when using standard python projects. For scientific packages I usually rely on conda. 
This is because conda is better at handling the various dependencies than pip is, especially for scientific packages. 
Many scientific packages officially recommend installation only as part of Anaconda.  
	Additionally, conda is a complete package, version and environment manager, which will take care 
	of not just python packages but also R etc, if your 
 project relies on more languages. Pip and venv are python specific. Currently the pip and the conda-forge branches are on par
 and will probably stay so, Sept 2017 onwards.
 
However, I will go with the official documentation and use pip, with a little modification.  
Official documentation instructs installing ni stats and nilearn using 

	(neuroimaging) > pip install -U nistats --user  (won't use this)
	(neuroimaging) > pip install -U nilearn --user  ( won't use this)
	
Using the --user switch installs the packages in the user's local python site packages directory instead of the system 
python. This is especially true for MacOS and Linux, which come with a standard python installation which we do not want to accidentally break.

However, since  am already doing all my installations in a conda virtual environment so i will not break anything. 
The --user flag will install the packages in my user site packages directory folder instead of my conda environment's 
directory. Hence I will skip that and do this:  
	
	(neuroimaging) > pip install -U nistats
	(neuroimaging) > pip install -U nilearn

The problem that I encountered with pip was that my new envhad no packages at all. Zero.   
This is not a usual use case, something that happened due to me fiddling with the packages
 and wanting a clean slate I am sure. HOwever it means that although I have all the necessary libraries installed 
 on my computer, they are not available for the new env to access. Which means I would have to install all necessary packages.
 
This is cumbersome in the extreme and while pip should handle it transparently, there is no `requirements.txt` file 
that I could find, which meant pip didn;t know the dependencies.

So I uninstalled thepip nilearn using

	(neuroimaging) > pip uninstall nilearn
	
and reintsalled it using conda from its conda-forge channel.

	(neuroimaging) > conda install nilearn -c conda-forge
	
That got me all the dependency packages I needed. The list of packages being installed will
scroll by. Nilearn will be the last package to be installed and here the process seemingly pauses
and takes some time before it completes.

The user guide uses an ipython notebook to showcase its examples. iPython is now jupyter notebook, so I went ahead and installed it:

	(neuroimaging) > conda install jupyter
	
Then run the jupyter notebook:

	(neuroimaging) > jupyter notebook
	
The notebook will start, you will see a bunch of messages, about 6-7 lines and then, something like:

	[I 20:11:22.111 LabApp] 0 active kernels
	[I 20:11:22.112 LabApp] The Jupyter Notebook is running at:
	[I 20:11:22.112 LabApp] http://localhost:8888/?token=a747ed6596f2586bd3a121e648836b3f3d606edb58efc7f4
	[I 20:11:22.112 LabApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
	[C 20:11:22.122 LabApp]

    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8888/?token=a747ed6596f2586bd3a121e648836b3f3d606edb58efc7f4
        
Copy paste the above URL in the browser window and press `ENTER`.  
Most likely, it will automatically open in the browser

As per the example in the user guide for nilearn, I did:

	from nilearn.datasets import MNI152_FILE_PATH
	print(f'Path to MNI152 template: {MNI152_FILE_PATH}')

and pressed `Ctrl + ENTER` to run the cell.  	
That gave me a warning: (don't worry about it)
(this wasnt in the notebook, but regular execution, the notebook did give me a warning as well.)

	~\Anaconda3\envs\neuroimaging\python.exe
	~/OneDrive/workspace/neuroimaging/higher_level_ui_example.py
	~\Anaconda3\envs\neuroimaging\lib\site-packages\h5py\__init__.py:36: 
		FutureWarning: Conversion of the second argument of issubdtype from `float` to `np.floating` is deprecated. 
		In future, it will be treated as `np.float64 == np.dtype(float).type`.
	from ._conv import register_converters as _register_converters

And then the output of the program:

	Path to MNI152 template: ~\Anaconda3\envs\neuroimaging\lib\site-packages\nilearn\datasets\data\avg152T1_brain.nii.gz
	
Ready to roll.

	from nilearn import image, plotting
	from nilearn.datasets import MNI152_FILE_PATH	
	
	print(f'Path to MNI152 template: {MNI152_FILE_PATH}')
	sample = MNI152_FILE_PATH
	plotting.plot_img(sample)
	
That gave me the output above and the signature of the plotting function, but no plot. I added this:

	from nilearn import image, plotting
	from nilearn.datasets import MNI152_FILE_PATH
	%matplotlib qt5                                     # Add this line.
		
	print(f'Path to MNI152 template: {MNI152_FILE_PATH}')
	sample = MNI152_FILE_PATH
	plotting.plot_img(sample)
				
Which gave me an interactive plot in a new window.  
I followed that up with:

	plotting.plot_glass_brain(sample)
	
 and ran the cell again, to get 2 plots this time.
Then I used the smoothing function and plotted the images:

	smoothed_img = image.smooth_img(sample, fwhm=5)
	print(smoothed_img)
	plotting.plot_img(smoothed_img)
	plotting.plot_glass_brain(smoothed_img)
 


### Some stuff I understood about conda, pip and pycharm:

First if you load the env in a terminal then pycharm can not access it until you deactivate it. I haven't tested if 
this happens from within pycharms terminal as well or just the external one.

Second if you pip install something while in a conda environment and the pip being used is not from that environment's 
files as well, then pip will install to the defualt site packages path, not restrict itself to the environment.  
You can check which pip is being used using `pip show pip` .  
If the path of the pip is the one that the environment is using (for example, `~/Anaconda3/envs/ileap_py36`) then 
you are fine.  
If it says something like `~/local/python/sitepackages` (you get the idea) then the pip being used is 
not part of the active/intended environment.  
To fix this, use conda to explicitly install pip in your environment, and then verify it.
