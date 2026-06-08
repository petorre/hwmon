# hwmon

## Install

```
sudo apt update
sudo apt install -y htop lm-sensors stress-ng
```

## Setup

```
sudo sensors-detect  # answer YES to all questions
sudo service kmod start
sudo modprobe coretemp
```

## Load

Start full utilization of vCPUs 0-3 with

```
taskset -c 0-3 stress-ng --cpu 4 --thermalstat 1
```

## Monitoring

In separate shells do

```
htop
```

```
watch -n 1 "clear; sensors;"
```

```
watch -n 1 "clear; sudo perf stat --timeout 1000 -e power/energy-pkg/,power/energy-cores/,power/energy-ram/;"
```
