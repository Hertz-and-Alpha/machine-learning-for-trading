# 설치 방법

> 2021년 4월 25일 업데이트:  [새로운 Zipline 버전](https://github.com/stefan-jansen/zipline-reloaded) 에서는 모든 운영 체제에서 도커 없이 백테스트 노트북을 실행할 수 있습니다.; 설치 지침은 이제 Windows/MacOS/Linux 환경 파일을 참조 하시면 됩니다.

> Update March 14, 2021: I have just released a [new Zipline version](https://github.com/stefan-jansen/zipline-reloaded) that runs on Python 3.7-3.9; see [release info](https://github.com/stefan-jansen/zipline-reloaded/releases/tag/2.0.0rc4) and [docs](https://zipline.ml4trading.io/). As a result, the Docker solution will no longer be necessary going forward and I will provide new environment files over the course of April.

> Update Feb 26, 2021: Release 2.0 reduces the number of environments to 2 and bumps the Python version to 3.8 for the main `ml4t` and to 3.6 for the `backtest` environment.
> Instructions below reflect these changes.
> 
> To update the Docker image to the latest version, run:
> ```docker pull appliedai/packt:latest```

이 책에서는 다음과 같이 설치할 수 있는 Python 3.8과 다양한 ML 및 거래 관련 라이브러리를 사용합니다.:

1.  [mamba](https://github.com/mamba-org/mamba)를 사용해서 [conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) 은  [Miniconda](https://docs.conda.io/en/latest/miniconda.html)를 기반으로  `ml4t.yml` 가상환경 설정 파일을 제공합니다.
2. Mac과 Linux 사용자들은 : via [pip](https://pip.pypa.io/en/stable/) Python venv를 이용해서, [pyenv](https://github.com/pyenv/pyenv) or [venv](https://docs.python.org/3/tutorial/venv.html)  `ml4t.txt` requirement files을 사용해서 설치.
3. [Docker](https://www.docker.com/)를 사용 [Docker Hub](https://www.docker.com/products/docker-hub)에서 이미지를 pull해야 되고 노트북을 실행하는 데 필요한 소프트웨어가 포함된 로컬 컨테이너를 생성합니다.

We'll describe how to obtain the source code and then lay out the first two options in turn. Then, we address how to work with [Jupyter](https://jupyter.org/) notebooks to view and execute the code examples. Finally, we list the legacy Docker installation instructions.

## 코드 샘플

[GitHub repository](https://github.com/stefan-jansen/machine-learning-for-trading), 이나 [cloning](https://www.howtogeek.com/451360/how-to-clone-a-github-repository/) 의 압축 버전을 다운로드하여 코드 샘플 작업을 수행할 수 있습니다. 후자는 커밋 기록을 포함하므로 다운로드 횟수가 더 많아집니다.
또는 리포트의 [fork](https://guides.github.com/activities/forking/) 를 생성하고 해당 컨텐츠를 복제한 후 계속 개발할 수 있습니다.

로컬로 코드를 실행시키려면 다음을 실행:
1. 코드와 데이터를 저장할 파일 시스템 위치를 선택합니다.
2. [GitHub 저장소](https://github.com/stefan-jansen/machine-learning-for-trading),에서 로그인 후 깃허브 레파지토리에서 다운로드 옵션을 사용하여 코드를 복제하거나 대상 폴더에 압축을 풉니다.
    - 코드를 복제하려면 CMD에서 git clone https://github.com/stefan-jansen/machine-learning-for-trading.git을 실행하고 새 디렉토리로 변경합니다. (깃허브가 없으시면 설치하세요!!)
    - 리포트를 복제하고 이름을 바꾸지 않은 경우 루트 디렉토리의 이름은 `machine-learning-for-trading`, the 이고 ZIP은 `machine-learning-for-trading-master`로 압축 해제됩니다.
   
   
   
## `conda`를 이용해서 필수 패키지 설치 

환경세팅은 아나콘다에 의존한다 [miniconda](https://docs.conda.io/en/latest/miniconda.html),  [mamba](https://github.com/mamba-org/mamba)는 패키지 매니징을 쉽게 해준다, 운영 체제마다 가상환경 생성 파일은 `installation/[windows|macos|linux]/ml4t.yml` 에 고정된 라이브러리 버전을 이용한다. 


또는 환경 파일 `installation/ml4t-base.yml` 에는 종속성이 없는 필수 라이브러리 목록만 포함되어 있습니다. 대신 이 파일을 사용하면 최신 버전을 사용할 수 있습니다. 어느 시점에서는 최신 소프트웨어가 예시와 호환되지 않을 수 있습니다.

관심 있는 노트북에 필요한 패키지만 설치하면 됩니다. 2021년 3월 최신 버전이 적용됩니다.


노트북은 먼저 설치해야 하는 [miniconda3](https://docs.conda.io/en/latest/miniconda.html)을 기반으로 하는 단일 가상 환경에 의존합니다.

다양한 운영 체제에 대한 자세한 지침은 [여기](https://conda.io/projects/conda/en/latest/user-guide/install/index.html)에서 확인할 수 있습니다.

### Environment file을 이용해서 Conda 가상환경 생성

[conda]는 [Anaconda](https://www.anaconda.com/) python 배포에서 제공하는 패키지 관리자입니다. 아쉽지만, 현재 문제가 있습니다 [not in very good shape](https://github.com/conda/conda/issues/9707). 대신에, [mamba](https://github.com/mamba-org/mamba)를 이용해서 패키지를 설치 할 수 있습니다. 아나콘다 prompt에서 아래 명령어를 실행 시킵니다:
```python
conda install -n base -c conda-forge mamba
```

[가상환경](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) 을 생성하려면 밑에 코드중에서 자신에 맞는 OS에 따라 코드를 실행시키면 됩니다. (e.g 윈도우이면 `mamba env create -f installation/windows/ml4t.yml` 실행

```bash
mamba env create -f installation/windows/ml4t.yml 
mamba env create -f installation/macosx/ml4t.yml 
mamba env create -f installation/linux/ml4t.yml 
```

가상 환경에 대한 자세한 설명은 [여기](https://towardsdatascience.com/getting-started-with-python-environments-using-conda-32e9f2779307)를 참조하십시오.

만약 최신 라이브러리로 생성을 원하면 아래 코드를 실행시키세요.

```bash
conda env create -f installation/ml4t-base.yml
```

### Conda 가상환경 실행

생성 후 이름을 사용하여 환경을 활성화할 수 있습니다. 이 이름은`ml4t` 입니다:

```bash
conda activate ml4t
```

가상환경을 종료시키고 싶으면 아래 코드를 실행시키세요


```bash
conda deactivate
```

## pip을 사용하여 라이브러리 설치

[가상 환경](https://realpython.com/python-virtual-environments-a-primer/)에 필요한 라이브러리를 설치해야 합니다. 여러 Python 버전을 병렬로 실행할 수 있는 기본 제공 [venv](https://docs.python.org/3/library/venv.html) 옵션 또는 [pyenv](https://github.com/pyenv/pyenv)를 참조하십시오.

일부 라이브러리에서는 시스템 상태에 따라 달라질 수 있는 OS별 소프트웨어를 이전에 설치해야 합니다. 아래에 몇 가지 일반적인 사례가 나열되어 있습니다. 다른 문제가 발생하는 경우 해당 문제의 원인이 되는 라이브러리에 대한 설명서를 참조하십시오. 이 방법으로 문제가 해결되지 않는 경우, GitHub에 문제를 제기하여 여기에 따라 지침을 확인하고 업데이트하십시오.

### MacOS: 사전 준비 사항

MacOS를 설치하려면 [homebrew](https://brew.sh/)를 통해 설치할 수 있는 다음 라이브러리가 필요합니다.
```bash
brew install lightgbm swig xz ta-lib
```

### Linux: 사전 준비 사항

Ubuntu 경우, `apt`를 사용할 수 있어야 된다. For TA-Lib, the [necessary steps](https://artiya4u.medium.com/installing-ta-lib-on-ubuntu-944d8ca24eae) are:

```bash
# nstall the build tool
sudo apt install build-essential wget -y

# Download and extract the source code
wget https://artiya4u.keybase.pub/TA-lib/ta-lib-0.4.0-src.tar.gz
tar -xvf ta-lib-0.4.0-src.tar.gz

# Config and build from source.
cd ta-lib/
./configure --prefix=/usr
make

# Install to system
sudo make install
```

### 요구 사항 설치

가상 환경을 생성하고 활성화했 OS에 따라 다음을 실행하면 됩니다.
```bash
pip install -U pip setuptools wheel
pip install -r installation/macosx/ml4t.txt # for macOS
pip install -r installation/linux/ml4t.txt # for Ubuntu
```

## 설치 후 해야될 것들

### QUANDL API Key 발급

다음 단계에서 책 전반에 걸쳐 몇 가지 예시로 사용할 미국 주식 데이터를 다운로드하려면 [register](https://www.quandl.com/sign-up)을 통해 개인 Quandl 계정을 통해 API 키를 얻으십시오. [프로파일](https://www.quandl.com/account/profile) 페이지에 표시됩니다.

Mac OSX와 같은 UNIX 기반 시스템에 있는 경우 QUANDL_API_KEY와 같은 환경 변수에 API 키를 저장할 수 있습니다. `export QUANDL_API_KEY=<your_key>`를 컴퓨터에 있는 `.bash_profile`.  에 추가

###  Zipline data 넣기

To run Zipline backtests, we need to `ingest` data. See the [Beginner Tutorial](https://zipline.ml4trading.io/beginner-tutorial.html) for more information. 

기본적으로 Zipline은 아래의 사용자 `~/.zipline` 디렉토리에 데이터를 저장합니다  

From the command prompt, activate your `ml4t` virtual environment and run:
```bash
zipline ingest -b quandl
``` 

You should see numerous messages (including some warnings that you can ignore) as Zipline processes around 3,000 stock price series.

### Working with Jupyter notebooks

This section covers how to set up notebook extension that facilitate working in this environment and how to convert notebooks to python script if preferred. 

#### Set up jupyter extensions

jupyter notebooks can use a range of [extentsion](https://github.com/ipython-contrib/jupyter_contrib_nbextensions) provided by the community. There are many useful ones that are described in the [documentation](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/).

The notebooks in this repo are formatted to use the [Table of Contents (2)](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/toc2/README.html) extension. For the best experience, activate it using the Configurator in the [Nbextensions](https://github.com/Jupyter-contrib/jupyter_nbextensions_configurator) tab available in your browser after starting the jupyter server. Modify the settings to check the option 'Leave h1 items out of ToC' if not set by default.

#### Converting jupyter notebooks to python scripts

The book uses [jupyter](https://jupyter.org/) notebooks to present the code with extensive commentary and context information and facilitate the visualization of results in one place. Some of the code examples are longer and make more sense to run as `python` scripts; you can convert a notebook to a script by running the following on the command line:

```bash
$ jupyter nbconvert --to script [YOUR_NOTEBOOK].ipynb
```

## Legacy Instructions: Running the notebooks using a Docker container

Docker Desktop is a very popular application for MacOS and Windows machines because is permits for the easy sharing of containerized applications across different OS. For this book, we have a Docker image that let's you instantiate a container to run Ubuntu 20.04 as a guest OS with the pre-installed [conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) on Windows 10 or Mac OS X without worrying about dependencies on your host.

### Installing Docker Desktop 

As usual, installation differs for Mac OS X and Window 10, and requires an additional step for Windows 10 Home to enable virtualization. 

We'll cover installation for each OS separately and then address some setting adjustments necessary in both cases.

#### Docker Desktop on Mac OS X

Installing Docker Desktop on Mac OS X is very straightforward:
1. Follow the detailed guide in Docker [docs](https://docs.docker.com/docker-for-mac/install/) to download and install Docker Desktop from [Docker Hub](https://hub.docker.com/editions/community/docker-ce-desktop-mac/). It also covers how Docker Desktop and Docker Toolbox [can coexist](https://docs.docker.com/docker-for-mac/docker-toolbox/).
2. Use [homebrew](https://brew.sh/) by following the tutorial [here](https://aspetraining.com/resources/blog/docker-on-mac-homebrew-a-step-by-step-tutorial).

Open terminal and run the following test to check that Docker works:
```Docker
docker run hello-world
```

Review the [Getting Started](https://docs.docker.com/docker-for-mac/) guide for Mac OS to familiarize yourself with key settings and commands.

#### Docker Desktop on Windows

Docker Desktop works on both Windows 10 Home and Pro editions; the Home edition requires the additional step of enabling the Virtual Machine Platform.  

##### Windows 10 Home: enabling the Virtual Machine Platform

You can now install Docker Desktop on Windows Home machines using the [Windows Subsystem for Linux](https://fossbytes.com/what-is-windows-subsystem-for-linux-wsl/) (WSL 2)  backend. Docker Desktop on Windows Home is a full version of Docker Desktop for Linux container development.

Windows 10 Home machines must meet certain [requirements](https://docs.docker.com/docker-for-windows/install-windows-home/#system-requirements). These include Windows 10 Home version 2004 (released May 2020) or higher. The Docker Desktop Edge release also supports Windows 10, version 1903 or higher.

Enable WSL 2 as described [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10), taking the following steps:

1. Enable the optional Windows Subsystem for Linux feature. Open PowerShell as Administrator and run:
    ```bash
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
   ```
2. Check that your system meets the requirements outlined [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10#requirements) and update your Windows 10 version if necessary.
3. Enable the Virtual Machine Platform optional feature by opening PowerShell as and Administrator and run:
    ```bash
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    ```
4. Restart your machine to complete the WSL install and update to WSL 2.
5. Download and run the Linux kernel [update package](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi). You will be prompted for elevated permissions, select ‘yes’ to approve this installation.
6. Set WSL 2 as your default version when installing a new Linux distribution by open PowerShell as Administrator and run the following command:
    ```bash
    wsl --set-default-version 2
    ```
  
##### Windows 10: Docker Desktop installation 

Once we have enabled WSL 2 for Windows Home, the remaining steps to install Docker Desktop are the same for Windows 10 [Home](https://docs.docker.com/docker-for-windows/install-windows-home/) and [Pro, Enterprise or Education](https://docs.docker.com/docker-for-windows/install-windows-home/). Refer to the linked guides for each OS version for system requirements.

1. Download and run (double-click) the installer from [Docker Hub](https://hub.docker.com/editions/community/docker-ce-desktop-windows/).
2. When prompted, ensure the Enable Hyper-V Windows Features option is selected on the Configuration page.
3. Follow the instructions on the installation wizard to authorize the installer and proceed with the install.
4. When the installation is successful, click Close to complete the installation process.
5. If your admin account is different to your user account, you must add the user to the docker-users group. Run Computer Management as an administrator and navigate to Local Users and Groups > Groups > docker-users. Right-click to add the user to the group. Log out and log back in for the changes to take effect.

Open Powershell and run the following test to check that Docker works:
```Docker
docker run hello-world
```

Review the [Getting Started](https://docs.docker.com/docker-for-windows/) guide for Windows to familiarize yourself with key settings and commands.

### Docker Desktop Settings: memory and file sharing 

The getting started guides for each OS referenced above describe the Docker Desktop settings.

#### Increasing memory 

- Under Preferences, look for Resources to find out how you can increase the memory allocated to the container; the default setting is too low given the size of the data. Increase to at least 4GB, better 8GB or more.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
- Several examples are quite memory-intensive, for example the NASDAQ tick data and the SEC filings example in Chapter 2, and will require significantly higher memory allocation.

#### Troubleshooting file sharing permissions

We will download the code examples and data to the local drive on your host OS but run it from the Docker container by mounting your local drive as a volume. This should work fine with the current versions but in case you receive **permission errors** , please refer to the **File Sharing** sections in the Docker user guides. The Docker GUIs let you assign permissions explicitly. See also (slightly outdated) explanation [here](https://rominirani.com/docker-on-windows-mounting-host-directories-d96f3f056a2c).
  
### Sourcing the code samples

You can work with the code samples by downloading a compressed version of the [GitHub repository](https://github.com/stefan-jansen/machine-learning-for-trading), or by [cloning](https://www.howtogeek.com/451360/how-to-clone-a-github-repository/) its content. The latter will result in a larger download because it includes the commit history. 

Alternatively, you can create a [fork](https://guides.github.com/activities/forking/) of the repo and continue to develop from there after cloning its content.

To work with the code locally, do the following:
1. Select a file system location where you would like to store the code and the data.
2. Using the `ssh` or `https` links or the download option provided by the green `Code` button on the [GitHub repository](https://github.com/stefan-jansen/machine-learning-for-trading), either clone or unzip the code to the target folder.
    - To clone the starter repo, run `git clone https://github.com/stefan-jansen/machine-learning-for-trading.git` and change into the new directory.
    - If you cloned the repo and did not rename it, the root directory will be called `machine-learning-for-trading`, the ZIP the version will unzip to `machine-learning-for-trading-master`.

### Get a QUANDL API Key

To download US equity data that we'll be using for several examples throughout the book in the next step, [register](https://www.quandl.com/sign-up) for a personal Quandl account to obtain an API key. It will be displayed on your [profile](https://www.quandl.com/account/profile) page.

If you are on a UNIX-based system like Mac OSX, you may want to store the API key in an environment variable such as QUANDL_API_KEY, e.g. by adding `export QUANDL_API_KEY=<your_key>` to your `.bash_profile`.  

### Downloading the Docker image and running the container

We'll be using a Docker [image](https://hub.docker.com/repository/docker/appliedai/packt) based on the Ubuntu 20.04 OS with [Anaconda](https://www.anaconda.com/)'s [miniconda](https://docs.conda.io/en/latest/miniconda.html) Python distribution installed. It comes with two conda environments described below. 

With a single Docker command, we can accomplish several things at once (see the Getting Started guides linked above for more detail):
- only on the first run: pull the Docker image from the Docker Hub account `appliedai` and the repository `packt` with the tag `latest` 
- creates a local container with the name `ml4t` and runs it in interactive mode, forwarding the port 8888 used by the `jupyter` server
- mount the current directory containing the starter project files as a volume in the directory `/home/packt/ml4t` inside the container
- set the environment variable `QUANDL_API_KEY` with the value of your key (that you need to fill in for `<your API key>`), and
- start a `bash` terminal inside the container, resulting in a new command prompt for the user `packt`.

1. Open a Terminal or a Powershell window.
2. Navigate to the directory containing the [ML4T](https://github.com/stefan-jansen/machine-learning-for-trading) code samples that you sourced above.
3. In the root directory of the local version of the repo, run the following command, taking into account the different path formats required by Mac and Windows:
    - **Mac OS**: you can use the `pwd` command as a shell variable that contains the absolute path to the present working directory (and you could use `$QUANDL_API_KEY` if you created such an environment variable in the previous step):  
        ```docker
        docker run -it -v $(pwd):/home/packt/ml4t -p 8888:8888 -e QUANDL_API_KEY=<your API key> --name ml4t appliedai/packt:latest bash
        ```
   - **Windows**: enter the absolute path to the current directory **with forward slashes**, e.g. `C:/Users/stefan/Documents/machine-learning-for-trading` instead of `C:\Users\stefan\Documents\machine-learning-for-trading`, so that the command becomes (for this example):                                                                                                                                                                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                                                                                                                                                  
     ```docker
     docker run -it -v C:/Users/stefan/Documents/machine-learning-for-trading:/home/packt/ml4t -p 8888:8888 -e QUANDL_API_KEY=<your API key> --name ml4t appliedai/packt:latest bash
     ```              
4. Run `exit` from the container shell to exit and stop the container. 
5. To resume working, you can run `docker start -a -i ml4t` from Mac OS terminal or Windows Powershell in the root directory to restart the container and attach it to the host shell in interactive mode (see Docker docs for more detail).

> To update the Docker image to the latest version, run:
> ```docker pull appliedai/packt:latest```

### Running the notebooks from the container

Now you are running a shell inside the container and can access both [conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html). Run `conda env list` to see that there are a `base`, `ml4t` (default), and a `backtest` environments.

The `backtest` environment is necessary because the latest version of Zipline 1.4.1 only support Python 3.6 and older versions of various other dependencies that partly also require compilation. I hope to update Zipline in the future to run on Python 3.8 as well.

We use the environment `ml4t` except for a dozen notebooks related to backtesting that use Zipline directly inputs generated by Zipline. The noteooks that require the `backtest` environment contain a notification. 

> If you want to use a GPU for the deep learning examples, you can run `conda install tensorflow-gpu` if you have the proper [CUDA version](https://www.tensorflow.org/install/source#gpu) installed. 
> **Alternatively**, you can leverage [TensorFlow's Docker](https://www.tensorflow.org/install/docker) images and install any additional libraries there; the DL examples don't require anything that's overly complicated to install.

- You can switch to another environment using `conda activate <env_name>` or using the Jupyter Notebook or Jupyter Lab Kernel menu thanks to the [nb_conda_kernels](https://github.com/Anaconda-Platform/nb_conda_kernels) extension (see below).
- You may see an error message suggesting you run `conda init bash`. After doing so, reload the shell with the command `source .bashrc`.

### Ingesting Zipline data

To run Zipline backtests, we need to `ingest` data. See the [Beginner Tutorial](https://zipline.ml4trading.io/beginner-tutorial.html) for more information. 

The image has been configured to store the data in a `.zipline` directory in the directory where you started the container (which should be the root folder of the starter code you've downloaded above). 

From the command prompt of the container shell, run
```bash
conda activate backtest
zipline ingest -b quandl
``` 
You should see numerous messages as Zipline processes around 3,000 stock price series.

#### Known Zipline issues

> I have patched the following country code issue in the [latest Zipline version](https://github.com/stefan-jansen/zipline/commit/b33e5c955a58d888f55101874f45cd141c61d3e1), so you should not have to manually fiddle with the asset database any longer.

When running a backtest, you will likely encounter an [error](https://github.com/quantopian/zipline/issues/2517) because the current Zipline version requires a country code entry in the exchanges table of the `assets-7.sqlite` database where it stores the asset metadata.

The linked [GitHub issue](https://github.com/quantopian/zipline/issues/2517) describes how to address this by opening the [SQLite database](https://sqlitebrowser.org/dl/) and entering `US` in the `country_code` field of the exchanges table.

In practice, this looks as follows:

1. Use the [SQLite Browser](https://sqlitebrowser.org/dl/) to open the file `assets-7.sqlite` in the directory containing your latest bundle download. The path will look like this (on Linux/Max OSX) if you ran the command as just described:  `~/machine-learning-for-trading/data/.zipline/data/quandl/2020-12-29T02;06;08.894865/`
2. Select the table `exchanges` as outlined in the following screenshot:
<p align="center">
<img src="https://i.imgur.com/khq6gtX.png" title="Modifying QUANDL SQLite - Step 1" width="50%"/>
</p>
3. Insert the country code and save the result (you'll get a prompt when closing the program):
<p align="center">
<img src="https://i.imgur.com/mtdiylk.png" title="Modifying QUANDL SQLite - Step 1" width="50%"/>
</p>

That's all. Unfortunately, you (had to..) repeat this everytime you run `zipline ingest -b quandl`. This error still occurs when you run `zipline ingest` for the default `quantopian-quandl` bundle because this command bypasses the `ingest` process and downloads instead a compressed version of the result generated by an earlier version of Zipline.  

### Working with notebooks int the Docker container

You can run [juypter](https://jupyter.org/) notebooks using either the traditional [notebook](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html) or the more recent [Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/) interface; both are available in all `conda` environments. Moreover, you start jupyter from the `base` environment and switch the environment from the notebook due to the `nb_conda_kernels` package (see [docs](https://github.com/Anaconda-Platform/nb_conda_kernels). 

To get started, run one of the following two commands:
```bash
jupyter notebook --ip 0.0.0.0 --no-browser --allow-root
jupyter lab --ip 0.0.0.0 --no-browser --allow-root
```
There are also `alias` shortcuts for each so you don't have to type them: 
- `nb` for the `jupyter notebook` version, and 
- `lab` for the `jupyter lab` version.

The container terminal will display a few messages while spinning up the jupyter server. When complete, it will display a URL that you should paste into your browser to access the jupyter server from the current working directory.

You can modify any of the environments using the standard conda workflow outlined below; see Docker [docs](https://docs.docker.com/storage/) for how to persist containers after making changes.  
