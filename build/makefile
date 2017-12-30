install:
  sudo apt-get install linux-headers-$(uname -r)
  sudo apt-get install -y tmux
  sudo apt-get install -y git
  sudo apt-get install -y cmake
  mkdir -p ~/sandbox
  mkdir -p ~/sandbox/miners

logstash: 
  wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
  sudo apt-get install apt-transport-https
  echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
  sudo apt-get update && sudo apt-get install logstash

nvidia-rig: install logstash
  wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.1.85-1_amd64.deb
  sudo dpkg -i cuda-repo-ubuntu1604_9.1.85-1_amd64.deb
  sudo apt-key adv --fetch-keys http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub
  sudo apt-get update
  sudo apt-get install -y cuda
  sudo apt-get install -y cuda-command-line-tools-9-1
  sudo apt-get install -y mesa-common-dev
  sudo apt-get install -y cuda-libraries-9-1

ethminer:
  rm -rf ~/sandbox/miners/ethminer
  git clone https://github.com/ethereum-mining/ethminer.git ~/sandbox/miners/ethminer
  mkdir -p ~/sandbox/miners/ethminer/build
  cd ~/sandbox/miners/ethminer/build; cmake -D CUDA_TOOLKIT_ROOT_DIR=/usr/local/cuda-9.1 -DETHASHCL=ON -DETHASHCUDA=ON ..
  cd ~/sandbox/miners/ethminer/build; cmake --build .
  cd ~/sandbox/miners/ethminer/build; sudo make install