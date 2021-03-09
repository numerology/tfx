# Penguin classification Example

**Warning: This code is experimental and is not ready for use. We welcome
feedback on this example.**

The Penguin classification example introduces the TFX programming
environment and shows you how to solve a classification problem using
TFX.

The Penguin classification example demonstrates the end-to-end workflow
and steps of how to classify penguin species.

## Instructions

Clone the tfx repo to the home directory and copy the penguin directory from the
tfx source to the home directory.

<pre class="devsite-terminal devsite-click-to-copy">
git clone https://github.com/tensorflow/tfx ~/tfx-source && pushd ~/tfx-source
cp -r ~/tfx-source/tfx/examples/penguin ~/
</pre>

Next, create a Python 3 virtual environment for this example and activate the
`virtualenv`:

<pre class="devsite-terminal devsite-click-to-copy">
virtualenv -p python3.7 penguin
source ./penguin/bin/activate
</pre>

Then, install the dependencies required by the Penguin example:

<pre class="devsite-terminal devsite-click-to-copy">
pip install tfx==0.26.1 \
  numpy==1.18.5 \
  scikit-learn==0.23.2
</pre>

### Local Example
Execute the pipeline python file. Output can be found at `~/tfx`:

<pre class="devsite-terminal devsite-click-to-copy">
python ~/penguin/experimental/penguin_pipeline_sklearn_local.py
</pre>

### GCP Example
Set the project id and bucket in `penguin_pipeline_sklearn_gcp.py`. Then, run the
following commands to copy the `~/penguin` directory to GCS and execute the
pipeline python file. Output can be found at `[BUCKET]/tfx` and metadata will
be stored in `~/tfx`:

<pre class="devsite-terminal devsite-click-to-copy">
vi ~/penguin/experimental/penguin_pipeline_sklearn_gcp.py
gsutil cp -r ~/penguin/data gs://[BUCKET]/penguin
gsutil cp -r ~/penguin/experimental gs://[BUCKET]/penguin
python ~/penguin/experimental/penguin_pipeline_sklearn_gcp.py
</pre>

Note that `gsutil cp -r ~/penguin/experimental gs://[BUCKET]/penguin` will need to be
run every time updates are made to `penguin_pipeline_sklearn_gcp.py`.
