> [!WARNING]  
> This Project is a work in progress and is not suitable to be used at this moment.  <br>
> The Processing algorithms are far from optimal and will undergo massive Improvements. <br>
> Star the repository for progress updates.

# Nano Image Server
![Rust-Linux Worklflow](https://github.com/mahinkumar/Nano_image_server/actions/workflows/Rust_Linux.yml/badge.svg)
![Rust-Windows Worklflow](https://github.com/mahinkumar/Nano_image_server/actions/workflows/Rust_Windows.yml/badge.svg)


<hr>

![image](https://github.com/user-attachments/assets/c43b43bf-b42e-4115-b225-da9a76f26894)
<hr>
Nano Image Server is a tiny, blazingly fast service to serve images with support for image operation on fly.

## Features
1. Low latency Image delivery
2. Image operation on fly via url queries
3. Support for GPU Acceleration
4. Simple Image browsing utility
5. Caching and Instant Retrieval
6. Support for Linux and Windows


## Usage

1. Place Images you need in images folder next to the executable
2. Start the server
```bash
./nano_image_server #Linux
start nano_image_server.exe #Windows
```
3. Access the server from port 8000 in localhost.
4. To get image go to `/image/<imagename>.<format>`
5. If needed resizing use queries resx and resy `/image/Nature.jpg?resx=1920&resy=1080`
6. When resizing use query resfilter `/image/Nature.jpg?resx=1920&resy=1080&resfilter=lanczos`
7. If specified size is 0 or left unspecified they display original size of the image
8. If resfilter query is unspecified, nearest is chosen by default
9. Choose from several resize algorithms for resizing using the resfilter query.<br>
    Availible resize algorithms are,
    - Nearest
    - Triangle
    - Catmullrom
    - Gaussian
    - Lanczos


## Version Benchmarks 
```markdown
# command
ab -n 1000 -c 24 -k 'http://localhost:8000/image/in.jpg?resx=1080&resy=1920' #With Processing
ab -n 1000 -c 24 -k 'http://localhost:8000/image/in.jpg' #Without Processing
```
### Nano_image_server With ApacheBench on 24 Threads (Balanced Power Mode on a Laptop)
![image](https://github.com/user-attachments/assets/a15ca744-08d2-4d65-8f08-ab62556ab752)

