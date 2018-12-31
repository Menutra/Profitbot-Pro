# teamredminer v0.3.8

This software is in a beta stage and may be unstable on some hardware.

Download is available in the [releases section](https://github.com/todxx/teamredminer/releases).

GPUs supported and tested:
- RX 580/570/480/470 on windows and linux with rocm or amdgpu-pro drivers
- RX Vega 64/56, Vega FE on windows and linux with rocm or amdgpu-pro/PAL drivers
- RX 560/550 on windows and linux with rocm or amdgpu-pro drivers

Software Requirements:
- A supported driver version (see GPUs Supported above)
- For cryptonight v8 on linux, only amdgpu-pro 18.30 and later drivers are supported.  ROCm is not supported.

This miner currently supports the lyra2z, phi2, and cryptonightv8/cnv2 algorithms.  Its only configuration is via command line to set the basic parameters for connecting to a stratum pool and selecting which platforms/devices to use.  Invoking the miner with the --help option will print a short help message for how to use the options.

The miner includes a read-only api based on the sgminer-5.5 API.  Both the json and text formats are supported.  For more details, we refer to the sgminer api documentation.  

This miner includes the following dev fees:
- Cryptonight v8: 2.5%
- Lyra2z:         3%
- Phi2:           3%

The miner reports GPU hash rates every 30 seconds.  These are the full GPU hash rates before dev fee deduction (your pool hashrate will be slightly lower). 

For reporting bugs and/or for features requests, please open an issue on this project's github [issue tracker](https://github.com/todxx/teamredminer/issues).

Happy hashing ;)

-----------
Changes in v0.3.8
- Added support for fan speed and temperatures.
- Added watchdog function for gpu init stuck, dead gpu, over-temp gpu, and non-responding pool.
- Added new optional 'L' config prefix for low-end cards like lexa/baffin for a 10+% speed-up on some cards
- Added an option for writing out a log file.
- Added cycling through multi-entry dns records when connecting to pools.
- Added a pool-connect timeout.
- Added measurement and displaying of pool response times.
- Added support for 80-byte headers for Phi2 algo (for non-LUX coins).
- Slightly tuned the '+' mode for polaris, some GPUs will show slight performance increase.
- Fixed bug with API interface occasionally getting stuck.

Changes in v0.3.7
- Redesigned GPU initialization, should now be less error prone.
- Added clean shutdown to reduce driver/GPU crashes.
- Added staggered GPU start-up to reduce GPU crashes.
- Added CPU verification for CNv8 and associated --no_cpu_check option.
- Fixed crash on pool authentication error.
- Added --pool_broken_rpc work-around option for pools that violate json rpc spec.
- Added option to reorder by PCIe bus numbers.
- Added --list_devices option to show available devices. 
- Added changed stats formatting to indicate which numbers are accepted/rejected/hw-error shares.
- Added uptime to stats.

Changes in v0.3.6
- Added support for Rx550 cards (gfx804).
- Improved stability on larger rigs, especially with weaker cpus.
- Improved error reporting on failed initialization.

Changes in v0.3.5
- Changed GPU initialization to be sequential by default and added --init_style option for faster init styles.
- Fixed network buffer size issue preventing the use of very long usernames/passwords/rig_ids.
- Added opencl platform auto-detection for AMD platforms when --platform is not specified.

Changes in v0.3.4
- Added CryptoNight v8 (CNv2) support
- Changed stats display to include pool hashrate and better formatting
- Added parallel GPU initialization
- Added output of submitted/accepted/rejected shares.
- Changed hashrate reported to be full GPU hashrate (previously hashrate reported was after dev fee deduction)

Changes in v0.3.3
- ROCm support reintroduced
- API support based on the sgminer API
- Improved GPU platform detection
- PCIe bus id printed on startup and is available over API
- Added option for periodic stats interval

Changes in v0.3.2
- Added windows support/build
- Added vega PAL driver support
- Removed ROCm support (temporarily)
- Removed libjansson dependency

Changes in v0.3.1
- Fixed phi2 issues causing rejected shares and low pool-side hashrate.

