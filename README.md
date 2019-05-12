# 3D-Model-Retrieval-COMS-6736-Visual-Database
COMS 6736 Visual Database Final Project
mkdir release 
cd release
cmake ..
make
make install

sse filelist -d static/dataset/ -p "*.jpg" -o ../../filelist
<br />
sse extract -f filelist -o features
<br />
sse vocabulary -f features -n 1000 -o vocabulary
<br />
sse quantize -v vocabulary -f features -o samples
<br />
sse extract_and_quantize -f filelist -v vocabulary -o samples
<br />
sse index -s samples -o index_file
<br />
