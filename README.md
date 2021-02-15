# til

Roadsigns along the way (normally found after hours of strife)

* 21-12-17: Docker for Mac default binds to 'no particular address' `0.0.0.0`, not to loopback `127.0.0.1`
* 22-01-18: PySpark might need `spark.executorEnv.PYTHONHASHSEED` set to a random int, as 3.3+/Spark 2+ doesn't seem to set this on the executors
* 25-01-18: If in client mode, PySpark will need to have `spark.driver.memory` set in init vs. at runtime (e.g. `spark-submit --driver-memory 10G`)
* 02-02-18: `s3(n/a)` filesystem support ships with Hadoop2.4, 2.5+ require additional `hadoop-aws` dependency
* 12-02-18: Keras (especially when booting on a fresh EC2 instance) will often need the env variables 
```
export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/cuda/lib64"
export CUDA_HOME=/usr/local/cuda
```
* 16-02-18: If `SettingWithCopyWarning` is being a PITA with `pandas`, stick in 
```
pd.options.mode.chained_assignment = None
```
* 21-11-18: `Docker`/`zsh` tab completion gist (https://gist.github.com/ro31337/b2c33ad0b90636e9e3bb76fb4fb76907)
* 22-11-18: I had no idea that `~` and `$HOME` weren't 100% interchangable https://stackoverflow.com/questions/11587343/difference-between-home-and-tilde
* 09-01-19: Removing a commit from history completely https://help.github.com/articles/removing-sensitive-data-from-a-repository/
* 11-01-19: I have no idea how many times I've written my own version of `more_itertools.windowed`, but it's [been in there since v2.5(!)](https://more-itertools.readthedocs.io/en/latest/api.html#windowing)
* 16-01-19: For `aws-cli` on a Mac, don't even both with the suggested `pip`-based install. `brew install awscli` works seamlessly
* 18-01-19: Had no idea Postgres was [over 20 years old](https://www.postgresql.org/docs/current/history.html)! 
* 29-01-19: Python's ternary operators can be really elegant
```python
a = 5
b = 'a < 5' if a < 5 else 'a >= 5'
print(b)
$ a >= 5
```
* 31-01-19: Always need to look this up: multi-instance edit in Sublime `cmd` + `ctrl` + `G`
* 24-07-19: Kill list of PIDs associated with an `lsof`/open files 
```
lsof -i :port | awk 'NR>1{print $2}' | xargs kill -9
```
* 28-08-19: [Build caching](https://medium.com/@aidobreen/using-docker-dont-forget-to-use-build-caching-6e2b4f43771e) of `Dockerfile`
* 27-11-19: `itertools.groupby` works on contiguous items(!), you probably [need to sort first](https://docs.python.org/3/library/itertools.html#itertools.groupby)
* 11-02-20: [`apply`: The convenience function you never needed](https://stackoverflow.com/a/54432584)
* 27-02-20: [`py4j`](https://www.py4j.org/) is brilliant 
* 06-03-20: [Why is _x_ named _x_?](https://wiki.debian.org/WhyTheName)
* 28-09-20: Software is hard
* 06-10-20: Installing `psycopg2` in OSX needs [some extra steps](https://blog.vince.id/installing-psycopg2-on-macos)
* 20-01-21: `pytest-xdist` distributes a test suite across available cores
```bash
pip install pytest-xdist
...
pytest -n auto
```
* 15-02-21: The `ports` command in `docker-compose` opens the container port to everything outside of the network. Not good, get it tae fuck
