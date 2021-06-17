### Some things occured when setting up this project:

* `project.clj` for the front-end needed to be extended to `:pedantic? false`. Otherwise it wouldn't build. Tested in 4 different environments.
* the app seems to serve tcp6 only? I wasn't able to run it locally following your documentation...
  (sorry, never used clojure before)
* part of my pipeline is a security check on docker images. I'm afraid that would fail atm:

```bash
[christian:~] work/fedora+ ± grype tw/asset-server:latest
 ✔ Vulnerability DB        [updated]
 ✔ Loaded image
 ✔ Parsed image
 ✔ Cataloged packages      [24 packages]
 ✔ Scanned image           [0 vulnerabilities]
No vulnerabilities found
[christian:~] work/fedora+ 22s ± grype tw/backend_feed:latest
 ✔ Vulnerability DB        [no update available]
 ✔ Loaded image
 ✔ Parsed image
 ✔ Cataloged packages      [70 packages]
 ✔ Scanned image           [15 vulnerabilities]
NAME             INSTALLED  FIXED-IN               VULNERABILITY        SEVERITY
commons-io       2.5        2.7                    GHSA-gwrp-pvrq-jmwv  Medium
commons-io       2.5        (fixes indeterminate)  CVE-2021-29425       Medium
glibc            2.33-r0    (fixes indeterminate)  CVE-2019-1010025     Medium
glibc            2.33-r0    (fixes indeterminate)  CVE-2021-27645       Low
glibc            2.33-r0    (fixes indeterminate)  CVE-2021-33574       Critical
glibc            2.33-r0    (fixes indeterminate)  CVE-2010-4756        Medium
glibc            2.33-r0    (fixes indeterminate)  CVE-2019-1010022     Critical
glibc            2.33-r0    (fixes indeterminate)  CVE-2019-1010023     High
glibc            2.33-r0    (fixes indeterminate)  CVE-2019-1010024     Medium
logback-classic  1.1.7      1.2.0                  GHSA-vmfg-rjjm-rjrj  Critical
logback-core     1.1.7      1.2.0                  GHSA-vmfg-rjjm-rjrj  Critical
rt               1.8.0_292  (fixes indeterminate)  CVE-2011-0009        Medium
rt               1.8.0_292  (fixes indeterminate)  CVE-2011-1007        Low
rt               1.8.0_292  (fixes indeterminate)  CVE-2011-1008        Medium
rt               1.8.0_292  (fixes indeterminate)  CVE-2011-2085        Medium
[christian:~] work/fedora+ 2s ± grype tw/backend_quote:latest
 ✔ Vulnerability DB        [no update available]
 ✔ Loaded image
 ✔ Parsed image
 ✔ Cataloged packages      [59 packages]
 ✔ Scanned image           [13 vulnerabilities]
NAME        INSTALLED  FIXED-IN               VULNERABILITY        SEVERITY
commons-io  2.5        2.7                    GHSA-gwrp-pvrq-jmwv  Medium
commons-io  2.5        (fixes indeterminate)  CVE-2021-29425       Medium
glibc       2.33-r0    (fixes indeterminate)  CVE-2021-27645       Low
glibc       2.33-r0    (fixes indeterminate)  CVE-2021-33574       Critical
glibc       2.33-r0    (fixes indeterminate)  CVE-2010-4756        Medium
glibc       2.33-r0    (fixes indeterminate)  CVE-2019-1010022     Critical
glibc       2.33-r0    (fixes indeterminate)  CVE-2019-1010023     High
glibc       2.33-r0    (fixes indeterminate)  CVE-2019-1010024     Medium
glibc       2.33-r0    (fixes indeterminate)  CVE-2019-1010025     Medium
rt          1.8.0_292  (fixes indeterminate)  CVE-2011-0009        Medium
rt          1.8.0_292  (fixes indeterminate)  CVE-2011-1007        Low
rt          1.8.0_292  (fixes indeterminate)  CVE-2011-1008        Medium
rt          1.8.0_292  (fixes indeterminate)  CVE-2011-2085        Medium
[christian:~] work/fedora+ 3s ± grype tw/frontend:latest
 ✔ Vulnerability DB        [no update available]
 ✔ Loaded image
 ✔ Parsed image
 ✔ Cataloged packages      [68 packages]
 ✔ Scanned image           [15 vulnerabilities]
NAME             INSTALLED  FIXED-IN               VULNERABILITY        SEVERITY
commons-io       2.5        2.7                    GHSA-gwrp-pvrq-jmwv  Medium
commons-io       2.5        (fixes indeterminate)  CVE-2021-29425       Medium
glibc            2.33-r0    (fixes indeterminate)  CVE-2019-1010023     High
glibc            2.33-r0    (fixes indeterminate)  CVE-2019-1010024     Medium
glibc            2.33-r0    (fixes indeterminate)  CVE-2019-1010025     Medium
glibc            2.33-r0    (fixes indeterminate)  CVE-2021-27645       Low
glibc            2.33-r0    (fixes indeterminate)  CVE-2021-33574       Critical
glibc            2.33-r0    (fixes indeterminate)  CVE-2010-4756        Medium
glibc            2.33-r0    (fixes indeterminate)  CVE-2019-1010022     Critical
logback-classic  1.1.7      1.2.0                  GHSA-vmfg-rjjm-rjrj  Critical
logback-core     1.1.7      1.2.0                  GHSA-vmfg-rjjm-rjrj  Critical
rt               1.8.0_292  (fixes indeterminate)  CVE-2011-0009        Medium
rt               1.8.0_292  (fixes indeterminate)  CVE-2011-1007        Low
rt               1.8.0_292  (fixes indeterminate)  CVE-2011-1008        Medium
rt               1.8.0_292  (fixes indeterminate)  CVE-2011-2085        Medium
[christian:~] work/fedora+ 2s ±


```

