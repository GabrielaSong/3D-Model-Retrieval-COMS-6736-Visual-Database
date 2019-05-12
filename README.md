# 3D-Model-Retrieval-COMS-6736-Visual-Database
COMS 6736 Visual Database Final Project
mkdir release 
cd release
cmake ..
make
make install

sse filelist -d static/dataset/ -p "*.jpg" -o ../../filelist
sse extract -f filelist -o features
sse vocabulary -f features -n 1000 -o vocabulary
sse quantize -v vocabulary -f features -o samples
sse extract_and_quantize -f filelist -v vocabulary -o samples
sse index -s samples -o index_file
