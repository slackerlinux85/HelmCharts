### this is a WIP and should not be considered ready ###

# Solariot

## Instructions ##
1. Install make a values.yaml file and change its values 
   `example values.yaml that will enable prometheus`
```YAML
  inverter:
    model: "sungrow-sg5kd"
    address: "192.168.1.230"
    port: 502
    slave: 0x01
    timeout: 3
    scan_interval: 10

  metrics:
    prometheus:
      enabled: true
      port: 8000

  serviceMonitor:
    enabled: true
    interval: "30s"
```
2. add helm repo

  `helm repo add solariot https://slackerlinux85.github.io/HelmCharts/`
  
3. dryrun solariot through helm and verify values

  `helm install -n <namespace> <release name> solariot/solariot -f <PathToYourValuesYamlFile.yaml> --dry-run`

4. install solariot through helm

  `helm install -n <namespace> <release name> solariot/solariot -f <PathToYourValuesYamlFile.yaml>`
  
5. cross your fingers and hope for the best!

## other example configs ##

* InfluxDB
```YAML
  inverter:
    model: "sungrow-sg5kd"
    address: "192.168.1.230"
    port: 502
    slave: 0x01
    timeout: 3
    scan_interval: 10

  metrics:
    influxdb:
      enabled: true
      address: "192.168.1.128"
      port: 8086
      username: "user"
      password: "password"
      db: "inverter"
      ssl: true
      verify_ssl: false
```

* MQTT
```YAML
  inverter:
    model: "sungrow-sg5kd"
    address: "192.168.1.230"
    port: 502
    slave: 0x01
    timeout: 3
    scan_interval: 10

  metrics:
    mqtt:
      enabled: true
      address: "192.168.1.128"
      port: 1883
      topic: "inverter/stats"
      username: "user"
      password: "password"
```
* PVOutput
```YAML
  inverter:
    model: "sungrow-sg5kd"
    address: "192.168.1.230"
    port: 502
    slave: 0x01
    timeout: 3
    scan_interval: 10

  metrics:
    pvoutput:
      enabled: true
      api: "api key"
      sid: "system-id"
      rate_limit: 60
```
