# Train Dataset Download
The train dataset is provided as a series of 7z archives. 

The size of the dataset is 120 GB and 18.8 GB compressed.
There are 6336 folders in the dataset, corresponding to the 6336 folders in the training set.


We provide a script to download and extract the files below.

You can download a small sample of the data [here](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_example.7z).

## Download
Below are the links to directly download each of the archive files.

- [Fusion360GalleryDataset_23hackathon_train.7z.001](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.001) (2 GB)
- [Fusion360GalleryDataset_23hackathon_train.7z.002](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.002) (2 GB)
- [Fusion360GalleryDataset_23hackathon_train.7z.003](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.003) (2 GB)
- [Fusion360GalleryDataset_23hackathon_train.7z.004](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.004) (2 GB)
- [Fusion360GalleryDataset_23hackathon_train.7z.005](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.005) (2 GB)
- [Fusion360GalleryDataset_23hackathon_train.7z.006](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.006) (2 GB)
- [Fusion360GalleryDataset_23hackathon_train.7z.007](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.007) (2 GB)
- [Fusion360GalleryDataset_23hackathon_train.7z.008](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.008) (2 GB)
- [Fusion360GalleryDataset_23hackathon_train.7z.009](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.009) (2 GB)
- [Fusion360GalleryDataset_23hackathon_train.7z.010](https://idetc23hackathon.s3.us-west-2.amazonaws.com/Fusion360GalleryDataset_23hackathon_train.7z.010) (1.2 GB)


## Extraction
To extract each archive requires a tool that supports the 7z compression format.

### Mac OS
On recent versions of Mac OS, 7z is supported natively.

### Windows
Windows users can download and install [7-Zip](https://www.7-zip.org), which offers both a GUI and command line interface.

### Linux
Distributions of Ubuntu come with `p7zip` installed. However, with older versions (e.g. 16.02) extraction times can be excessively slow. If you experience extraction times of longer than 10 mins per archive, we suggest using the latest version provided on the [7-Zip](https://www.7-zip.org) website. The following commands can be used to download and install the latest version if not already available in your package manager:

```
curl https://www.7-zip.org/a/7z2106-linux-x64.tar.xz -o 7z2106-linux-x64.tar.xz
sudo apt install xz-utils
tar -xf 7z2106-linux-x64.tar.xz
```
and then extract the archives:
```
7zz x Fusion360GalleryDataset_23hackathon_train_00.7z 
```

## Download and Extraction Script
We provide the python script [train_dataset_download.py](train_dataset_download.py) to download and extract all archive files. 

### Installation
The script calls [7-Zip](https://www.7-zip.org) directly so if you encounter problems, ensure the path is set correctly in the `get_7z_path()` function or `7z` is present in your linux path. To run the script you will need the following python libraries that can be installed using `pip`:

- `requests`
- `tqdm`


### Running
The script can be run by passing in the output directory where the files will be extracted to. 

```
python train_dataset_download.py --output path/to/files
```
Additionally the following optional arguments can be passed:
- `--limit`: Limit the number of archive files to download.
- `--threads`: Number of threads to use for downloading in parallel [default: 4].
- `--download_only`: Download without extracting files.

The script will not re-download and overwrite archive files that have already been downloaded.
