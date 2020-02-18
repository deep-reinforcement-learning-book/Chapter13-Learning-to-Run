# Chapter 13: Learning to Run (Project 1)
## Description:
Example of solving [*NIPS 2017: Learning to Run* challenge](https://www.crowdai.org/challenges/nips-2017-learning-to-run) with paralleled Soft Actor-Critic (SAC) algorithm. 
<p align="center">
<img src="https://github.com/deep-reinforcement-learning-book/Chapter14-Learning-to-Run/blob/master/figures/learning2run.gif" width="40%">
</p>

## Dependencies:
* osim-rl: install the osim-rl environment following [here](https://github.com/stanfordnmbl/osim-rl) or using the [docker](https://hub.docker.com/r/stanfordnmbl/opensim-rl) (`docker pull stanfordnmbl/opensim-rl`)
* PyTorch

The environment dependencies can be installed as follows with a new conda env (opensim-rl):

```python
# 1. Create a conda environment with the OpenSim package.
conda create -n opensim-rl -c kidzik opensim python=3.6.1

# 2. Activate the conda environment we just created.
# On windows, run:
activate opensim-rl

# On Linux/OSX, run:
source activate opensim-rl

# 3. Install our python reinforcement learning environment.
conda install -c conda-forge lapack git
pip install osim-rl

# 4. Git clone the Nips2017 environment and our solution.
git clone https://github.com/deep-reinforcement-learning-book/Project1-RL-for-Learning-to-Run
```

If installed correctly, run following script should start the env:

```python
from osim.env import RunEnv
env = RunEnv(visualize=True)
observation = env.reset(difficulty = 0)
for i in range(200):
    observation, reward, done, info = env.step(env.action_space.sample())
```



## Contents:
* `osim/`: the original version of osim-rl for *NIPS 2017: Learning to Run* challenge, osim-rl environments have been updated and no longer provide 2017 version through direct package installation;
* `figures/`: figures for displaying;
* `model/`: models after training;
* `sac_learn.py`: pralleled Soft Actor-Critic algorithm for solving *NIPS 2017: Learning to Run* task;
* `reward_log.npy`: log of episode reward during training;
* `plot.ipynb`: displaying the learning curves.


## Usage:
1. Run `$ python sac_learn.py --train` for training the policy

2. Run `$ python sac_learn.py --test` for testing the trained policy, remember to change the `trained_model_path` for testing your own model, which is default to be the trained model we provided.

3. The training process will provide a `reward_log.npy` file for recording the reward value during training, which can be displayed with `$ jupyter notebook` in a new terminal, choose `plot.ipynb`and Shift+Enter, as follows:
<p align="center">
<img src="https://github.com/deep-reinforcement-learning-book/Chapter14-Learning-to-Run/blob/master/figures/training.png" width="80%">
</p>

## Authors:
[Zihan Ding](https://github.com/quantumiracle), [Yanhua Huang](https://github.com/Officium)


## Citing:

```
@misc{DeepReinforcementLearning-Chapter13-LearningtoRun,
  author = {Zihan Ding, Yanhua Huang},
  title = {Chapter13-LearningtoRun},
  year = {2019},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/deep-reinforcement-learning-book/Chapter13-Learning-to-Run}},
}
```
