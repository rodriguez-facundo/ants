FROM base-ants:latest

LABEL maintainer="Facundo Rodriguez <facundo@metacell.us>"

#-------------------------------------------------------------------------------
# ANTsPY
#-------------------------------------------------------------------------------
# Install ANTsPY with IDK and VTK

RUN pip install ${ANTPY_GIT}

#-------------------------------------------------------------------------------
# dcm2niix
#-------------------------------------------------------------------------------
# Convert DICOM to NIfTY 

RUN mkdir -p ${ANTPATH} &&\
    curl -L $DCM2NIIX_HTTP | bsdtar -xzf - -C ${ANTPATH}

# Copy data and some notebooks
COPY --chown=1000:100 dicom_pet dicom_pet
COPY --chown=1000:100 Hammers Hammers
COPY --chown=1000:100 pet.ipynb pet.ipynb
COPY --chown=1000:100 Plotting.ipynb Plotting.ipynb
COPY --chown=1000:100 Segmentation.ipynb Segmentation.ipynb
COPY --chown=1000:100 Co-registration.ipynb Co-registration.ipynb
COPY --chown=1000:100 pydicome.ipynb pydicome.ipynb
COPY --chown=1000:100 mnc2nii.ipynb mnc2nii.ipynb

CMD ["jupyter", "notebook", "--NotebookApp.token=''"]
