# Changelog
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]
### Changed
### Added
- `hc run` now looks for the --interface flag or `HC_INTERFACE` env var if you want to specify the `http` interface [#846]((https://github.com/holochain/holochain-rust/pull/779)
- Scenario API added to enable deterministic scenario tests for zome functions. See the [NodeJS Container README](nodejs_container/README.md) for details.
- Admin RPC functions added to container interface. Any (websocket) container interface that is configured with 
  `admin = true`  now can call the following functions to remotely change any aspect of the container config
  (intended to be used in an upcoming container admin UI):
  * `admin/dna/install_from_file` (install a DNA from a local file)
  * `admin/dna/uninstall`
  * `admin/dna/list`
  * `admin/instance/add`
  * `admin/instance/remove`
  * `admin/instance/start`
  * `admin/instance/stop`
  * `admin/instance/list` (list of all instances in config)
  * `admin/instance/running` (list of currently running instances)
  * `admin/interface/add` (starts the interface)
  * `admin/interface/remove` (stops the interface)
  * `admin/interface/add_instance` (restarts the interface to get change in effect)
  * `admin/interface/remove_instance` (restarts the interface to get change in effect)
  * `admin/interface/list`
  * `admin/agent/add`
  * `admin/agent/remove`
  * `admin/agent/list`
  * `admin/bridge/add`
  * `admin/bridge/remove`
  * `admin/bridge/list`
  
  See rustdoc of `container_api::interface::ContainerApiBuilder` for a full description of these functions. 
  

### Removed

## [0.0.3] - 2019-01-15
### Fixed
- build problems because of changes to upstream futures-preview crate
### Added
- Networking: beyond mock, using [n3h](https://github.com/holochain/n3h)
- Bridging now works and is configurable in the container (no capabilities yet) [#779](https://github.com/holochain/holochain-rust/pull/779) & [#776](https://github.com/holochain/holochain-rust/pull/776)
- Validation across network [#727](https://github.com/holochain/holochain-rust/pull/727)
- API/HDK:
    - CRUD for entries working
    - Node-to-node messaging [#746](https://github.com/holochain/holochain-rust/pull/746)
    - GetEntryOptions:
        - retrieve CRUD history & status
        - meta data: sources
    - GetLinksOptions
        - meta data: sources
    - GetLinks helpers: get_links_and_load
    - Query: return multiple entry types with glob matching [#781](https://github.com/holochain/holochain-rust/pull/781)
- Container:
    - configuration builder and config files
    - http interface [#823](https://github.com/holochain/holochain-rust/pull/823)
- hc command-line tool:
    - `run --persist` flag for keeping state across runs [#729](https://github.com/holochain/holochain-rust/pull/729/files)
    - Added env variables to activate real networking [#826](https://github.com/holochain/holochain-rust/pull/826)
- Groundwork for: capabilities & signals [#762](https://github.com/holochain/holochain-rust/pull/826) & [#732](https://github.com/holochain/holochain-rust/pull/732)
- Improved debug logging with log rules and colorization [#819](https://github.com/holochain/holochain-rust/pull/819)
- This change log!

### Changed
- API/HDK:
    - native return types (JsonStrings)
    - many places where we referred to "Hash" we now use the more correct term "Address"

## [0.0.2] - 2018-11-28
### Added
- mock networking
- `hc run` with support for
- multi-instance scenario testing
