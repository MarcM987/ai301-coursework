# Contribution: [Issue Title]

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Marc Martinez
**GitHub Username:** MarcM987
**Issue:** https://github.com/meshtastic/firmware/issues/8213
**Pull Request:** [GitHub PR link, once opened]

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Built the issue-scout overlay and a profile-driven search strategy for first contributions in the wild**

I built the scout using search requests that gather all things compatible with my profile, at least one search per profile sentence; this was a search for literal compatibility.
Then I decided the ranking of those results by the content of the profile, setting preferences for my strengths and desired work using words likely found in each subject to match: strongest in C/Python, growth goals in C++/assembly, signals/security, computer vision, and data science. 
I also made sure to drop any results with assignees or those that seemed stale; and ordered by fewer comments first, but with at least one comment.
What broke was the unaticipated inclusion of repo forks, throw away repos, and issues requiring hardware, so what changed was a revision of the rubric and evidence guide to account for each directly.


**Unit 6: Installed the voice-guard overlay, patched the rubric, and wrote a local repo-memory file for meshtastic/firmware**

[2-4 sentences: the voice-guard, the repo-memory file. What broke or
fell short, and what changed because of it. "Nothing broke" counts when
it is true - say how you know.]

Promoted the voice guard as instructed then created the repo-memory file with guidance on the contribution policy, test requirements, scope, and relevant subsystem.
I gave the memory file my current insights regarding the specifc location of behavior as well based on my reproduction and other issue comments.
I also made sure to add a note to keep the work honest and properly styled.


**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I searched for this issue using the AI301 Issue Selection tool as required. 
However, I filtered for languages I was familiar with, issues specific to bugs, and organizations that I know and support.
My scan surfaced that I should double check that this is still an issue as the devlopment branch is on a newer version, which I subseqently did confirm on the latest release.
My scout produced an accept verdict on the issue. 
This issue also fits my profile because it plays on my strengths: C/C++ and Python, while also aligning with my profile's interest in security.
That is essentially what I hope to gain from working on this issue, using what I know while simultaneously pushing my comfort zone to grow, in this case towards security which is an area I'm hoping to grow in.

The scout did fairly well in all areas, until I created an interesting edge case for it.
A previous issue I was exploring proved to be already resolved during my reproduction and the maintainer agreed, so the tool had to contend with passing or failing an issue that I commented on, resolved, and was confirmed by the maintainer and discussed to be closed. 
My rubric was never meant to deal with the confusion of "no assignees" (informal or formal), but also informally resolved by the me, the user; It was also never meant to grade closed issues; it passed, with no evidence on assignees, arguably it should have failed on both metrics.
Both of these are edge cases that I would consider in my rubric, adding a check both to ensure the issue is open and also not informally resolved, even without a specific "claim".

Claimed: https://github.com/meshtastic/firmware/issues/8213#issuecomment-6423112343

**Toolkit**

- Tool: issue-scout (Patched for the wild according to unit 6, search-strategy.md to check for issues specific to my profile + rubric.md to check validity of the repo and the issue), I used it to both find issues that may be relevent to my skillset and interests and also to then grade issues that I select from curation.
- What it produced: It produced a verdict of accept for this issue and noted that it fits my desired growth areas to help me improve in both C++ and Security regarding its references to SSL certs. It gave it the difficulty of "Straightforward".
- Difficulties: It didn't handle the edges cases of already resolved issues very well for the other issues.
- What changed: The difficulty adjustment in scope via the patch. And I would update both the rubric and the evidence guide to consider scernios more common to resolved issues and not just the behaviors around open issues.

---

## Understanding the Issue

**Problem Description**

When running meshtasticd with the --sim flag, so that it runs in simulation mode, SSL certificates fail to be read or created.
Similarily, the synergistic issue also noted with this is that the Webserver never starts.

**Expected Behavior**

Upon starting meshtasticd in sim mode, SSL certificates should be successfully created and/or read, then the Webserver should start accordingly.

**Current Behavior**

Starting meshtasticd in sim mode never creates or reads SSL certificates and never starts the Webserver.

**Affected Components**

The affected area of the codebase is contained within `src/platform/portduino/PortduinoGlue.cpp`.
Specifically the sections regarding the setting of configuration settings around the sim setting parameters.

**Toolkit**

- Tool: Manual Review of the issue's stated relevant code section.
- What it produced: An understanding of the SSL certificate and Webserver configuration behaviors
- Difficulties: Deciphering the difference between intentional and unintentional behaviors.
- What changed: I have a better understanding of where to begin implementations.

---

## Reproduction Process

**Environment Setup**

No challenges other than dependancies. The build will stop and explain a missing tool if the scenario is encountered. 
This dependacy list worked for my machine.

Ubuntu 26.04.1 LTS
Meshtastic: 2.8.2.eaba8b9, commit: eaba8b95b, newer build used as the issue has not been addressed or resolved, and is still present.
PlatformIO Core: 6.2.0

```bash
sudo apt update && sudo apt install -y \
  build-essential g++ pkg-config git python3-pip python3-venv \
  libgpiod-dev libyaml-cpp-dev libjsoncpp-dev libbluetooth-dev \
  libusb-1.0-0-dev libi2c-dev libuv1-dev libxkbcommon-dev \
  libinput-dev libsqlite3-dev libbsd-dev \
  openssl libssl-dev libulfius-dev liborcania-dev \
  libsdl2-dev libcurl4-gnutls-dev

python3 -m venv venv
source .venv/bin/activate
pip install -U platformio
```

```bash
gh repo clone MarcM987/firmware
cd firmware
git checkout develop
git submodule update --init --recursive
pio run -e native
sudo mkdir -p /etc/meshtasticd/ssl
sudo cp ./bin/config-dist.yaml /etc/meshtasticd/config.yaml
```

** /etc/meshtasticd/config.yaml ** , everything else is default, module Sim is to enable SimRadio
```yaml
...
Lora:
    Module: Sim
...
Webserver:
    Port: 9443
    RootPath: /usr/share/meshtasticd/web
    SSLKey: /etc/meshtasticd/ssl/private_key.pem
    SSLCert: /etc/meshtasticd/ssl/certificate.pem
...
```

**Steps to Reproduce**

1. Install and Setup the Environment As Above
2. Verify Correct Behavior

Deleting certificates between runs, to ensure clean start to each test.
```bash
sudo rm /etc/meshtasticd/ssl/*.pem
```

```bash
sudo ./.pio/build/native/meshtasticd 
```
```bash
Portduino is starting, VFS root at /root/.portduino/default
Using /etc/meshtasticd/config.yaml as config file
MAC ADDRESS: 9C:B6:D0:0B:66:E2
ERROR | ??:??:?? 0.001 No radio instance available to provide entropy
Initializing extra pins
Portduino critical error: Failed to open posix file /dev/spidev0.0, errno=2
No hardware spi chip found...
WARN  | 11:20:16 0.074 RTC set: not found (addr 0x00)
WARN  | 11:20:16 0.074 RTC read: not found (addr 0x00)
INFO  | 11:20:16 0.074 

//\ E S H T /\ S T / C

INFO  | 11:20:16 0.074 No I2C device configured, Skip
INFO  | 11:20:16 0.074 No I2C devices found
INFO  | 11:20:16 0.074 S:B:37,2.8.2.eaba8b9,native,MarcM987/firmware
INFO  | 11:20:16 0.074 Build timestamp: 1793170800
INFO  | 11:20:16 0.074 Init NodeDB
INFO  | 11:20:16 0.074 Load /prefs/nodes.proto
INFO  | 11:20:16 0.074 Loaded /prefs/nodes.proto
INFO  | 11:20:16 0.074 Loaded saved nodedatabase v25: 1 nodes, 0 pos, 0 tel, 0 env, 0 status
/root/.portduino/default/prefs/warm.dat does not exist
INFO  | 11:20:16 0.074 Load /prefs/device.proto
INFO  | 11:20:16 0.075 Loaded /prefs/device.proto
INFO  | 11:20:16 0.075 Loaded saved devicestate v25
INFO  | 11:20:16 0.075 Load /prefs/config.proto
INFO  | 11:20:16 0.075 Loaded /prefs/config.proto
INFO  | 11:20:16 0.075 Loaded saved config v25
ERROR | 11:20:16 0.075 Invalid channel index 0 > 0, malformed packet received?
INFO  | 11:20:16 0.075 Load /prefs/module.proto
INFO  | 11:20:16 0.075 Loaded /prefs/module.proto
INFO  | 11:20:16 0.075 Loaded saved moduleConfig v26
INFO  | 11:20:16 0.075 Load /prefs/channels.proto
INFO  | 11:20:16 0.075 Loaded /prefs/channels.proto
INFO  | 11:20:16 0.075 Loaded saved channelFile v26
/root/.portduino/default/prefs/uiconfig.proto does not exist
ERROR | 11:20:16 0.075 Can't open/read /prefs/uiconfig.proto
INFO  | 11:20:16 0.076 Wanted region 0, using UNSET
INFO  | 11:20:16 0.076 Sort took 0 ms
INFO  | 11:20:16 0.076 Save /prefs/nodes.proto
INFO  | 11:20:16 0.076 TransmitHistory: loaded 1 entries from disk
WARN  | 18:20:16 0.076 RTC read: not found (addr 0x00)
INFO  | 18:20:16 0.076 [TM] Config: nodeinfo_max_hops=0 rate_window=0s rate_max=0 unknown_thresh=0 pos_interval=21600s
INFO  | 18:20:16 0.076 [TM] Allocating unified cache: 2048 entries (20480 bytes)
/root/.portduino/default/prefs/hopScalingState.bin does not exist
/root/.portduino/default/prefs/cannedConf.proto does not exist
ERROR | 18:20:16 0.076 Can't open/read /prefs/cannedConf.proto
INFO  | 18:20:16 0.076 CannedMessageModule is enabled
WARN  | 18:20:16 0.076 DMShell enabled on Portduino: remote shell access is dangerous and intended for trusted debugging only
INFO  | 18:20:16 0.076 DMShell: bounding unacknowledged output to 4 frames
INFO  | 18:20:16 0.076 External Notification Module Disabled
INFO  | 18:20:16 0.076 Start meshradio init
INFO  | 18:20:16 0.076 Radio freq=906.875, config.lora.frequency_offset=0.000
INFO  | 18:20:16 0.076 Set radio: region=UNSET, name=LongFast, config=0, ch=19, power=30
INFO  | 18:20:16 0.076 newRegion->freqStart -> newRegion->freqEnd: 902.000000 -> 928.000000 (26.000000 MHz)
INFO  | 18:20:16 0.076 numFreqSlots: 104 x 250.000kHz
INFO  | 18:20:16 0.076 channel_num: 20
INFO  | 18:20:16 0.076 frequency: 906.875000
INFO  | 18:20:16 0.076 Slot time: 44 msec, preamble time: 131 msec
INFO  | 18:20:16 0.076 sim init success
ERROR | 18:20:16 0.076 Error reading File : /etc/meshtasticd/ssl/certificate.pem 
ERROR | 18:20:16 0.076 SSL Certificate File can't be loaded or missing
INFO  | 18:20:16 0.117 Create SSL Key /etc/meshtasticd/ssl/private_key.pem successful
INFO  | 18:20:16 0.117 Create SSL Cert /etc/meshtasticd/ssl/certificate.pem successful
INFO  | 18:20:16 0.117 Use webserver port from yaml config 9443 
INFO  | 18:20:16 0.117 Webserver started
INFO  | 18:20:16 0.119 Web Server framework started on port: 9443 
INFO  | 18:20:16 0.119 Web Server root /usr/share/meshtasticd/web
INFO  | 18:20:16 0.119 API server listen on TCP port 4403
INFO  | 18:20:16 0.119 PowerFSM init, USB power=1
INFO  | 18:20:16 0.119 MemAudit[boot]: msgstore=4400 warm=80000 nodedb=20000 satmaps=0 pkthist=10048 tmm=20480 total=134928
INFO  | 18:20:16 0.119 [Power] Power: battery hardware absent (USB-only)
INFO  | 18:20:46 30.076 [HOPSCALE] hop=7 util=0% nodes=0 samp=1/1 filt=1/1
INFO  | 18:20:46 30.076 [NodeInfo] Send our nodeinfo to mesh (wantReplies=0)
INFO  | 18:20:46 30.076 [NodeInfo] Send owner !3af077d8/Meshtastic 66e2/66e2
INFO  | 18:20:46 30.208 [SimRadio] tophone queue status queue full, discard oldest
INFO  | 18:21:16 60.076 [TM] Preloaded 0 next-hop hints from NodeDB
```

```bash
ls /etc/meshtasticd/ssl/
```
```bash
certificate.pem  private_key.pem
```

```bash
sudo ss -tulpn | grep -E '4403|9443'
```
```bash
tcp   LISTEN 0      5                                 0.0.0.0:4403       0.0.0.0:*    users:(("meshtasticd",pid=43426,fd=12))    
tcp   LISTEN 0      4096                              0.0.0.0:9443       0.0.0.0:*    users:(("meshtasticd",pid=43426,fd=11))
```

3. Reproduced Issue

```bash
sudo rm /etc/meshtasticd/ssl/*.pem
```

```bash
sudo ./.pio/build/native/meshtasticd --sim
```
```bash
Portduino is starting, VFS root at /root/.portduino/default
Running in simulated mode.
ERROR | ??:??:?? 0.001 No radio instance available to provide entropy
DEBUG | ??:??:?? 0.077 Upgrade time to quality NTP
WARN  | 10:12:50 0.077 RTC set: not found (addr 0x00)
WARN  | 10:12:50 0.077 RTC read: not found (addr 0x00)
DEBUG | 10:12:50 0.077 RTC net quality reached (None -> NTP), reconciling rx_time
INFO  | 10:12:50 0.077 

//\ E S H T /\ S T / C

INFO  | 10:12:50 0.077 No I2C device configured, Skip
INFO  | 10:12:50 0.077 No I2C devices found
DEBUG | 10:12:50 0.077 acc_info = 0
DEBUG | 10:12:50 0.077 mag_info = 0
INFO  | 10:12:50 0.077 S:B:37,2.8.2.eaba8b9,native,MarcM987/firmware
INFO  | 10:12:50 0.077 Build timestamp: 1793170800
INFO  | 10:12:50 0.077 Init NodeDB
INFO  | 10:12:50 0.077 Load /prefs/nodes.proto
INFO  | 10:12:50 0.077 Loaded /prefs/nodes.proto
INFO  | 10:12:50 0.077 Loaded saved nodedatabase v25: 1 nodes, 0 pos, 0 tel, 0 env, 0 status
/root/.portduino/default/prefs/warm.dat does not exist
INFO  | 10:12:50 0.077 Load /prefs/device.proto
INFO  | 10:12:50 0.077 Loaded /prefs/device.proto
INFO  | 10:12:50 0.077 Loaded saved devicestate v25
INFO  | 10:12:50 0.077 Load /prefs/config.proto
INFO  | 10:12:50 0.078 Loaded /prefs/config.proto
INFO  | 10:12:50 0.078 Loaded saved config v25
ERROR | 10:12:50 0.078 Invalid channel index 0 > 0, malformed packet received?
INFO  | 10:12:50 0.078 Load /prefs/module.proto
INFO  | 10:12:50 0.078 Loaded /prefs/module.proto
INFO  | 10:12:50 0.078 Loaded saved moduleConfig v26
INFO  | 10:12:50 0.078 Load /prefs/channels.proto
INFO  | 10:12:50 0.078 Loaded /prefs/channels.proto
INFO  | 10:12:50 0.078 Loaded saved channelFile v26
/root/.portduino/default/prefs/uiconfig.proto does not exist
ERROR | 10:12:50 0.078 Can't open/read /prefs/uiconfig.proto
DEBUG | 10:12:50 0.078 cleanupMeshDB purged 0 entries
DEBUG | 10:12:50 0.078 Use nodenum 0x3af077d8 
DEBUG | 10:12:50 0.078 Regenerate PKI public key from private key
DEBUG | 10:12:50 0.079 Set DH private key for crypto operations
DEBUG | 10:12:50 0.079 Expand short PSK #1
INFO  | 10:12:50 0.079 Wanted region 0, using UNSET
DEBUG | 10:12:50 0.079 Coerce telemetry to role-aware min on defaults
INFO  | 10:12:50 0.079 Sort took 0 ms
DEBUG | 10:12:50 0.079 Save to disk 16
DEBUG | 10:12:50 0.079 Opening /prefs/nodes.proto, fullAtomic=0
INFO  | 10:12:50 0.079 Save /prefs/nodes.proto
INFO  | 10:12:50 0.079 TransmitHistory: loaded 1 entries from disk
Portduino critical error: Failed to open posix file /dev/spidev0.0, errno=2
No hardware spi chip found...
DEBUG | 10:12:50 0.079 Use compiled/slipstreamed tzplaceholder                                         
DEBUG | 17:12:50 0.079 Set Timezone to GMT0
WARN  | 17:12:50 0.079 RTC read: not found (addr 0x00)
DEBUG | 17:12:50 0.079 Start multicast thread
INFO  | 17:12:50 0.080 [TM] Config: nodeinfo_max_hops=0 rate_window=0s rate_max=0 unknown_thresh=0 pos_interval=21600s
INFO  | 17:12:50 0.080 [TM] Allocating unified cache: 2048 entries (20480 bytes)
DEBUG | 17:12:50 0.080 [TM] NodeInfo cache not available on this target
/root/.portduino/default/prefs/hopScalingState.bin does not exist
/root/.portduino/default/prefs/cannedConf.proto does not exist
ERROR | 17:12:50 0.080 Can't open/read /prefs/cannedConf.proto
INFO  | 17:12:50 0.080 CannedMessageModule is enabled
WARN  | 17:12:50 0.080 DMShell enabled on Portduino: remote shell access is dangerous and intended for trusted debugging only
INFO  | 17:12:50 0.080 DMShell: bounding unacknowledged output to 4 frames
INFO  | 17:12:50 0.080 External Notification Module Disabled
DEBUG | 17:12:50 0.080 Activate sim radio on SPI port 
INFO  | 17:12:50 0.080 Start meshradio init
INFO  | 17:12:50 0.080 Radio freq=906.875, config.lora.frequency_offset=0.000
INFO  | 17:12:50 0.080 Set radio: region=UNSET, name=LongFast, config=0, ch=19, power=30
INFO  | 17:12:50 0.080 newRegion->freqStart -> newRegion->freqEnd: 902.000000 -> 928.000000 (26.000000 MHz)
INFO  | 17:12:50 0.080 numFreqSlots: 104 x 250.000kHz
INFO  | 17:12:50 0.080 channel_num: 20
INFO  | 17:12:50 0.080 frequency: 906.875000
INFO  | 17:12:50 0.080 Slot time: 44 msec, preamble time: 131 msec
INFO  | 17:12:50 0.080 sim init success
INFO  | 17:12:50 0.080 API server listen on TCP port 4403
DEBUG | 17:12:50 0.080 LoRA bitrate = 118.394310 bytes / sec
INFO  | 17:12:50 0.080 PowerFSM init, USB power=1
INFO  | 17:12:50 0.080 MemAudit[boot]: msgstore=4400 warm=80000 nodedb=20000 satmaps=0 pkthist=10048 tmm=20480 total=134928
DEBUG | 17:12:50 0.080 Node status update: 0 online, 1 total
INFO  | 17:12:50 0.080 [Power] Power: battery hardware absent (USB-only)
INFO  | 17:13:20 30.131 [HOPSCALE] hop=7 util=0% nodes=0 samp=1/1 filt=1/1
INFO  | 17:13:20 30.131 [NodeInfo] Send our nodeinfo to mesh (wantReplies=0)
DEBUG | 17:13:20 30.131 [NodeInfo] Skip send NodeInfo since we sent it <1800s ago
INFO  | 17:13:50 60.089 [TM] Preloaded 0 next-hop hints from NodeDB
INFO  | 17:14:20 90.150 [DeviceTelemetry] Send: air_util_tx=0.000000, channel_utilization=0.000000, battery_level=101, voltage=0.000000, uptime=90
DEBUG | 17:14:20 90.150 [DeviceTelemetry] Initial packet id 692397083
DEBUG | 17:14:20 90.150 [DeviceTelemetry] Node status update: 0 online, 1 total
INFO  | 17:14:20 90.150 [DeviceTelemetry] Send packet to phone
INFO  | 17:14:20 90.150 [DeviceTelemetry] Sending local stats: uptime=90, channel_utilization=0.000000, air_util_tx=0.000000, num_online_nodes=0, num_total_nodes=1, noise_floor=-120
INFO  | 17:14:20 90.150 [DeviceTelemetry] num_packets_tx=0, num_packets_rx=0, num_packets_rx_bad=0
```

```bash
ls /etc/meshtasticd/ssl/
```
```bash
(no output)
```
```bash
sudo ss -tulpn | grep -E '4403|9443'
```
```bash
tcp   LISTEN 0      5                                 0.0.0.0:4403       0.0.0.0:*    users:(("meshtasticd",pid=34531,fd=10))
```
4. Observed Results
## Expected
Missing SSL certificates to be created and webserver started and listening on port 9443, as well as the API server on port 4403
## Actual
Missing SSL certificates never created and webserver never started; API Server starts without issue on port 4403.

**Reproduction Evidence**

- **Commit showing reproduction:** None
- **Screenshots/logs:** Logs in the above reproduction guide
- **My findings:**  The config.yaml file is never loaded in sim mode, and thus the ssl and web server confirgurations are never applied.
    A work around for this is to specifically load it instead of relying on default loading, but whether this is intended or not needs clarification from the maintainer.

**Toolkit**

- Tool: repro-check (Checked my reproduction report and made sure there were no gaps)
- What it produced: It accepted my report with minor suggestions regarding improved language
- Difficulties: It unexpectedly nitpicked the fact I was working from my fork of the firmware and not the main repo.
- What changed: I claified in my report that they are currently at the same commit, so working from mine is now understood to not be an issue.

---

## Solution Approach

**Analysis**

The issue is being caused because the configuration for the Webserver is never set, which in turn means the SSL certiifcates are not processed.
This root cause is in `portduinoSetup` in `src/platform/portduino/PortduinoGlue.cpp`.
The config loading if-else chain intentionally skips reading any config.yaml files when in sim mode, but when this change was made SSL and Webserver functionality were not considered.

**Proposed Solution**

I am deliberately not changing the intended functionality of the if-else chain, as the maintainers explicitly seem to want that functionality.
My proposed fix is to instead add the minimum critical configuration for the Webserver to function in a seperate code block that sets sim defaults.

**Implementation Plan**

1. Modify `src/platform/portduino/PortduinoGlue.cpp` to also set the defaults for Webserver in sim mode
2. Add the default Webserver port 9443 and root path to sim defaults configuration block at `if (portduino_config.force_simradio){`, defaults apply only when webserverport == -1.
3. Rebuild and re-run the reproduction steps and capture the evidence.
4. Manually check that the SSL cerrtifcates are created and read & that the Webserver starts properly as configured, as there is no test suite for these functionalities.
5. Run the complete test suite for the build to ensure no other functionalities are negatively impacted by the change. 

Risk:
Potential for port collision when running many instances of sim.


Issue was discovered to be resolved by a change in design implementations on an unmentioned and unreferenced PR #11348; found through manual investigation of a seemingly relevant code comment that turned out to be extremely relevant. 
Resolving this issue in anyway, including in my successfully tested implementation to minimally configure Webserver by default, is a design decision.

**Toolkit**

- Tool: plan-check
- What it produced: Fail on honesty.
- Difficulties: The tool checks did not take into account visual/manual review and affects honesty.
- What changed: Need to update rubric to allow for edge cases that have no formal test cases implemented.

---

## Testing Strategy

The reproductions steps were re-run both pre and post build change.
The SSL certification read/creation, as well as the Webserver functionality were verified through the log outputs and manual verification of certificates and Webserver access via browser.
The repo's built in test suite was also run pre and post build change to verify that no other functionalities or behaviors were negatively impacted.

**Toolkit**

- Tool: bin/run-tests.sh
- What it produced: All tests pass
- Difficulties: These tests don't strictly pertain to my issue's behavior and more so check the integrity of other functional systems.
- What changed: Nothing changed, confirmed manual visual review is needed for resolving this issue.

---

## Implementation Notes

**10/29/2026**
Issue stems from missing configurations in for the webserver that cause it not to load and thus not read/create SSL certificates. 
Adding minimum configurations for port and root path

**10/29-30/2026** (worked over-night)
Minimum configurations set load behaviors to start webserver and resolves the issue.
Behavior manually reviewed and full build compiled and test suite ran compared against test suite on clean build; Success, Ready for PR.
Default configurations changed? Webserver now starts on default just as standard non-simulated run, is this intended? Investigating.

**10/30/2026**
Investigated relevant configuration code sections, discovered non-issue related PR discussing non loading of configuration in sim mode as intentional design; PR #11348.
Issue is a design decision in current build, not a bug. Waiting for response from maintainer for implementing the resolving change or closing of the issue without a PR.

**Toolkit**

- Tool: Research and Communicate (Research discussions of behavioral changes discussed between maintainers and reached  out for clarification)
- What it produced: A clear understanding of bug vs feature dynamics, awaiting response.
- Difficulties: Unlinked and undocumented behavioral changes can sneak into other issues quietly, this was one such issue.
- What changed: Resolving this issue should no longer be done without clear determinations from the maintainers.

---

## Pull Request

**PR Link:** https://github.com/meshtastic/firmware/issues/8213

**PR Description:** No PR, the issue was resolved by a recent design decision. 
So the best PR is simply closing the issue or waiting for a maintainer to direct regarding another design change.

**Maintainer Feedback:**

- [10/29/2026]: No Response from the mainainer yet. 

**Status:** Awaiting review.

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

I learned that there is a fine line between a bug and feature.
Code can be correct absolutely, but if the results of that code are not to the intention of the hollistic design or even minor decsisons by those in charge then the code is still fundamentally incorrect.
Integrity here means not continuing without maintainer direction once you've discovered your correct code is potentially unintended.
The skill gained, the knowledge that researching the codebase and documents is not always enough, sometimes the social aspects of understanding communications that may implicitly determine behaviors is just as important.

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

Contrary to the workflow we've undergone, I would actually do a precursory investigation and plan before fully committing to shortcircuit this problem in the future.
Our Current Workflow: Selection-Reproduction-Plan-Implement-Pull Request
My New Workflow: Selection-Reproduction-Issue Investigation-PrePlan-Plan-Implement-Pull Request
Where: 
Issue Investigation is to breifly review the issue and the relevant codebase or documentation to answer the question- is this still a bug or has the recent build made it more so a design consideration? Done after reproduction as fully understanding the relevent behavior is critical in determining this.
PrePlan is to do a cursory plan check, before wrtiing a report and doing numerous checks, simply go over the logic in your head and over the codebase and documentation to answer the question- would resolving this require a change in behaviors other than the specific bug/issue? would it require a change in documentation such that it must considered before use? these questions would strongly indicate whether or not resolving the issue requires a design consideration. (I do not mean how a specific plan may answer these question, but instead how any plan would).

Simply put, my relfection sums to an addition of extra caution and research of both formal and informal channels. Observing the material present at the specific issue at hand may not be enough.

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
