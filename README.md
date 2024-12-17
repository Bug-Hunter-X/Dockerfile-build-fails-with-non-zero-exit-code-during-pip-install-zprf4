# Dockerfile Build Failure
This repository demonstrates a common issue encountered when building Docker images: a non-zero exit code during the package installation phase. The original Dockerfile fails to build successfully due to a problem with pip installing dependencies.  The solution offers a corrected version that addresses potential causes such as missing dependencies or permission problems, providing a more robust and reliable build process.

## Bug Description
The Dockerfile, as initially written, uses `apt-get update` and `apt-get install` to set up the necessary system packages, then proceeds to install Python requirements from `requirements.txt` using `pip3`.  However, the build process fails with a non-zero exit code, indicating that `pip3` is unable to install all the requirements successfully.

## Solution
The corrected Dockerfile includes several improvements to ensure a successful build:

1. **Explicit Dependency Resolution:** It is improved by explicitly specifying the Python version for pip (using `python3 -m pip`).
2. **Enhanced Error Handling:** The `pip install` command is improved to provide more verbose output during the installation process.
3. **Cleanup:** Added `apt-get clean` and `rm -rf /var/lib/apt/lists/*` to clean up unnecessary files after installing dependencies to reduce the image size.
4. **User Permissions:** Using a non-root user improves security in the Dockerfile.

By implementing these changes, the Docker image builds successfully.