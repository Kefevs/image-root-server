### Custom Image Registry

**Image root server designed for file-based source feeding**

- **Local Image Server**: Acts as a root proxy registry server, pulling its images directly from a local folder rather than over a network.
- **Optimized for Low-Bandwidth Environments**: Reduces the complexity of setting up a container registry in environments with limited or unreliable bandwidth.
- **Automated Image Handling**: Includes scripts for loading and managing images from `.tar.gz` files, streamlining deployment.
- **Compressed Image Saving**: Provides a script (`save-images.sh`) for saving Podman images as compressed `.tar.gz` files for storage and efficient distribution.
- **Configurable Registry**: Supports flexible configuration through YAML files, automatically adjusting paths and settings based on the registry version.
- **Multi-Port Setup**: Operates using separate internal and public-facing ports for enhanced control over image loading and access (5001 for internal, 5000 for public).
- **Buildah Integration**: Utilizes `buildah` for pulling, tagging, and pushing images, making it fully compatible with Podman-native workflows.
- **Version-Responsive Configuration**: Automatically selects the correct configuration path based on the major version of the registry.
- **Health Check Ready**: Built-in health checks ensure the registry is up and running, verifying image availability through HTTP endpoints.

### Environmental Variables

- **`OTEL_TRACES_EXPORTER`**: Disables OpenTelemetry traces by default.
  - Default: `none`

- **`REGISTRY_STORAGE_FILESYSTEM_ROOTDIRECTORY`**: Defines the root directory where the registry stores its images.
  - Default: `/var/lib/registry`

- **`REGISTRY_HTTP_SECRET`**: HTTP secret used for the Docker registry.
  - Default: `SWA`

- **`DISTRIBUTION_CONFIG`**: Path to the distribution configuration file, based on the registry version.
  - Default: `/etc/distribution/config.yml`

- **`LOAD_FILE_PATH`**: Directory path where image tarballs are stored for loading into the registry.
  - Default: `/opt/images`

- **`CONFIG_PATH`**: Configuration file path for running the registry. It defaults to `/etc/distribution/config.yml` if not set.
  - Default: `/etc/distribution/config.yml`

- **`CONFIG_PATH_REGULAR`**: Path to the public-facing configuration file.
  - Default: `/etc/distribution/config.yml`

- **`CONFIG_PATH_INTERNAL`**: Path to the internal configuration file used for image loading.
  - Default: `/opt/config/config-internal.yml`


