# ansible-r-ci

Run the playbook using: <br />
```
ansible-playbook -i localhost, r-ci.yml
```

### System requirements

Use the `sysreqs` variable to specify a comma separated list of system
requirements that must be present. <br />
Example: <br />
```
ansible-playbook -i localhost, --extra-vars "sysreqs=gdal-devel,geos-devel,proj-devel,sqlite-devel" r-ci.yml
```

### Static code analysis of R code

Default is to run static code analysis of the R code using
[lintr](https://lintr.r-lib.org/).  Set `r_ci_lintr=false` to disable
this check. <br />
Example: <br />
```
ansible-playbook -i localhost, --extra-vars "r_ci_lintr=false" r-ci.yml
```

### Code coverage

Use the `r_ci_covr` variable to run [covr](https://covr.r-lib.org/) on
a package and specify the target for the code coverage report. <br />
Valid targets are: <br />
- `azure`: output the result so it is available on Azure Pipelines
- `codecov`: upload the result to codecov.io
- `coveralls`: upload the result to coveralls
- `gitlab`:  create report for GitLab
- `standalone`: output the result to a local file 'covr.html'

Example, run code coverage and output the result to 'covr.html': <br/>
```
ansible-playbook -i localhost, --extra-vars "r_ci_covr=standalone" r-ci.yml
```
