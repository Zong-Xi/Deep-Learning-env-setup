# Deep-Learning-environment-setup
record some setup steps in ubuntu16.04

------------------------------
* Ubuntu16.04
* RTX 2080
* CUDA 10.0 + Cudnn 7.6.5
* Tensorflow


# Gym-Gazebo Installation



# Some Problem
## OpenAI Gym 
`env.render()` -> `*** Error in python': corrupted size vs. prev_size ***`
solve: 
```
sudo apt-get install libtcmalloc-minimal4
export LD_PRELOAD="/usr/lib/libtcmalloc_minimal.so.4"
```
