

Launch a ubuntu server with Jupyter using conda

Download and install conda
``wget https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh
sudo bash Anaconda3-2019.03-Linux-x86_64.sh``

Try
``conda``

If command is not found, change the PATH
``export PATH=~/anaconda3/bin:$PATH``

Start Jupyter notebook
``jupyter notebook --ip=0.0.0.0 --no-browser``

Go to your jupyter notebook (don't forget to allow port 8888 in SG)
3.82.222.81


Create a virtual environnement:
``conda create -n nameofyourenv python=3.6``

I don't know what that do:
"This needs to be done outside your virtual env
``conda install nb_conda``

Go into your virtual env
``conda activate cyril``

note: If an error message say that the conda Init is not activate, just relaunch a terminal

Install Ipykernel to install packages
``conda install ipykernel``

Create your kernel
``ipython kernel install --user --name=cyrilb``

# Install Git
``sudo apt-get install git``

# Clone the folder of leodsti
``git clone https://github.com/Cyril-Basquin/AWS_Tutorials-1.git``

# Install all the package
``pip install -r AWS_Tutorials-1/MNIST/requirements.txt``

# Launch the notebook 00-mnist-cnn.ipynb using your created kernel


#For the Application Server installation
#I recommend using an Ubuntu AMI
git clone https://github.com/leodsti/AWS_Tutorials.git
cd AWS_Tutorials/MNIST/
sudo apt-get update
sudo apt-get install python3-pip.
