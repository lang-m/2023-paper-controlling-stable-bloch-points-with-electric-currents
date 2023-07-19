FROM mambaorg/micromamba:git-675aa44-bookworm

USER root

# libgl1-mesa-glx required for dolfinx import
# xvfb required for pyvista in notebook for Fig. 1
RUN apt-get -y update && apt-get install -y git libgl1-mesa-glx xvfb && rm -rf /var/lib/apt/lists/*

ADD . /tmp/
RUN chown -R $MAMBA_USER .

USER $MAMBA_USER

RUN micromamba install -y -n base -f environment.yml && micromamba clean --all --yes

ENV PATH /opt/conda/bin:$PATH

RUN oommf +version
RUN python -c "import dolfinx; print(dolfinx.__version__)"
RUN python -c "import gmsh; print(gmsh.platform.platform())"

# check notebooks run without errors
# pyvista plotting in this notebook requires a running X-Server
RUN export DISPLAY=:99; Xvfb $DISPLAY -screen 0 1024x768x16 -nolisten tcp -nolisten unix & 2>&1 >> /dev/null; jupyter-nbconvert --to notebook --execute Fig-1-Fig-3-Fig-4_single-notch/2_Fig1_current-density.ipynb
RUN jupyter-nbconvert --to notebook --execute Fig-1-Fig-3-Fig-4_single-notch/4_Fig-3_Fig-4.ipynb
RUN jupyter-nbconvert --to notebook --execute Fig-2_rectangular-strip/3_Fig-2.ipynb
RUN jupyter-nbconvert --to notebook --execute Fig-5_multi-notch-single-BP/3_Fig-5.ipynb
RUN jupyter-nbconvert --to notebook --execute Fig-6_multi-notch-multi-BP/3_Fig-6.ipynb
RUN jupyter-nbconvert --to notebook --execute Fig-7_T-shaped-geometry/3-Fig-7.ipynb

# check that all image files have been created
RUN [ -f Fig-1-Fig-3-Fig-4_single-notch/Fig1.svg ] || exit 1
RUN [ -f Fig-1-Fig-3-Fig-4_single-notch/Fig3.pdf ] || exit 1
RUN [ -f Fig-1-Fig-3-Fig-4_single-notch/Fig4.pdf ] || exit 1
RUN [ -f Fig-2_rectangular-strip/Fig2.pdf ] || exit 1
RUN [ -f Fig-5_multi-notch-single-BP/Fig5.pdf ] || exit 1
RUN [ -f Fig-6_multi-notch-multi-BP/Fig6.pdf ] || exit 1
RUN [ -f Fig-7_T-shaped-geometry/Fig7.pdf ] || exit 1

