#+STARTUP: content
* WebStorm License
** webstorm license server http://15.idea.lanyus.com/
* Shell Commands
** echo "enable 0;">/proc/alog
** Signature
*** java -jar out/host/linux-x86/framework/signapk.jar build/target/product/security/platform.x509.pem build/target/product/security/platform.pk8 out/target/product/amoi89_wet_jb2/obj/APPS/DoulBatteryServices.apk.unsigned out/target/product/amoi89_wet_jb2/obj/APPS/DoulBatteryServices.apk.signed
*** java -jar -Xmx2048m /home/workspace/scripts/fotazip/cmd/updateTools/signapk.jar -w /home/workspace/scripts/fotazip/cmd/updateTools/zopo/v7/release/keys/testkey.x509.pem /home/workspace/scripts/fotazip/cmd/updateTools/zopo/v7/release/keys/testkey.pk8 V2.1.0-R-20131001.2018.zip V2.1.0-R-20131001.2018-signed.zip
** MK
*** ./mk_aliphone.sh x2 eng adb new false YUNOS_PROGUARD=false
*** ./mk_aliphone.sh x2 user acb new true CODEBASE_VERSION=3.0
*** ./mk_aliphone.sh i966 eng adb new false CODEBASE_VERSION=3.0
** scp config
*** sudo apt-get install ssh
*** sudo iptables -L
** umount [device is busy]
*** fuser -km [mount-point]
** Manufacture Mode
*** *#*#564548#*#*
*** *#*#3646633#*#*
*** *#369#
** Ubuntu oracle-java
*** sudo add-apt-repository ppa:webupd8team/java
*** sudo apt-get update
*** sudo apt-get install oracle-java7-installer
** Monkey Command
*** monkey -p com.yunos.alicontacts -p com.android.phone -p com.android.incallui -p com.android.server.telecom --ignore-crashes --ignore-security-exceptions --ignore-timeouts --pct-trackball 0 --pct-nav 0 --pct-majornav 0 --pct-anyevent 0  -v -v -v --throttle 500 1200000000 > /mnt/sdcard/monkey_phone.log 2>&1 &
*** monkey -p com.yunos.alicontacts -p com.android.incallui -p com.android.phone -p  --ignore-crashes --ignore-timeouts --ignore-security-exceptions --pct-trackball 0 --pct-nav 0 --pct-majornav 0 --pct-anyevent 0 -v -v -v --throttle 500 1200000000 > /mnt/sdcard/monkeysyslog.log 2>&1 &
*** monkey --ignore-crashes --ignore-timeouts --ignore-security-exceptions --pct-trackball 0 --pct-nav 0 --pct-majornav 0 --pct-anyevent 0 -v -v -v --throttle 500 1200000000 > /mnt/sdcard/monkeysys.log 2>&1 &
** Procstate
*** monkey --ignore-crashes --ignore-timeouts --ignore-security-exceptions --pct-trackball 0 --pct-nav 0 --pct-majornav 0 --pct-anyevent 0 -v -v -v --throttle 500 1200000000 > /mnt/sdcard/monkeysys_all.log 2>&1 &
*** sleep 7200 && dumpsys procstats --details --hours 4 > /sdcard/procstats.log &
*** dumpsys procstats --details --hours 48 > /sdcard/procstats.log &
** BSP Make
*** source build/envsetup.sh
*** lunch full_ali6735m_35gc_l-user
*** make -j24 2>&1 | tee build.log
** VNC command
*** vncserver start -geometry 1920x1080
** Android AMT
*** amt record /var/log/1.txt
*** amt stop
*** amt play
** 4.0
*** Commands
**** sendlink page://keyguard.yunos.com/KeyguardService -e [start|stop|restart] -d [pin|pattern]
**** sendlink page://keyguard.yunos.com/KeyguardService -e restart -d pattern
*** cd xmake
*** ./configure --with-platform=phone --with-product=l5pro --with-board=mtk && source xdirs
*** ./mk_yunos.sh sc9832 userdebug run_inside_container $_host
*** Ctnr: ./mk_yunos.sh sc9832_m <build_type> run_inside_container new <host_code_absolute_dir>
*** Host: ./configure --with-platform=phone --with-product=sc9832_m --with-board=sprd --with-buildtype=<build_type>
*** mm
*** memleak
    + python MemLeak.py -d phone -p page://cardshell.yunos.com/cardshell -s script/cardshell_upslide_2.txt -r 100 -j
    + python MemLeak.py -d phone -p page://settings.yunos.com/settings -s script/ime.yunos.com.txt -r 100 -j
    + python MemLeak.py -d phone -V 4 -p com.android.phone -s script/ime.yunos.com.txt -r 100 -j
    + procrank  | grep -e scim -e keyboard
      PID       Vss      Rss      Pss      Uss  cmdline
      3561   354636K   36892K   16824K   12156K  page://ime.yunos.com/keyboard
      663    45064K   15796K   14529K   14332K  /usr/lib/scim-1.0/scim-launcher
    + agilcmd --log_itemcount [pid]
      05-30 14:13:06.550 D/AGIL    ( 3561): current item number:982
*** result
    + 14606   315960K   28380K   12486K    7804K  page://ime.yunos.com/keyboard
      728    55280K   11400K   10570K   10412K  /usr/lib/scim-1.0/scim-launcher
** V8 Profiling
*** process.startCPUProfile("setting");
*** process.stopCPUProfile("setting", "/opt/data/root/settings.yunos.com/start.cpuprofile");
*** adb -host pull /opt/data/root/settings.yunos.com/start.cpuprofile .
*** rm -rf ./mnt/data/yunos/opt/data/root/ime.yunos.com/local/setting.json
** Host Debug
*** adb -host shell weston-dumpsys
*** adb shell dumpsys window
*** adb logcat -v threadtime | grep "KeyguardServiceDelegate"
** Host heapdump
*** vmcmd --heapdump-self [pid]
*** PATH: /mnt/data/yunos/var/log/pid-xxxx.v8snapshot
** MemLeak
*** ./MemLeak.py -d phone -p page://keyguard.yunos.com/KeyguardService -s script/keyguard_passwd_unlock.txt -r 100 -j --only_js
*** _pid=`adb -host shell busybox ps | egrep '\bkeyguard\b' | cut -c1-6` && echo "keyguard pid:"$_pid && adb -host shell vmcmd --force-gc $_pid && sleep 2 && adb -host shell showmap $_pid
** Unit test
*** adb -host shell "cd /mnt/data/yunos/opt/app/keyguard.yunos.com && jasmine"
** HTC_LINK
*** adb -host shell sendlink page://firstexp.yunos.com/FirstExp -d OceanA20170323
*** sendlink page://yunbrowser.yunos.com/browser -d {\"action\":\"LOAD_URL\",\"url\":\"www.baidu.com\",\"isNewTabForeground\":true}
*** sendlink page://yunbrowser.yunos.com/browser -d {\"action\":\"LOAD_URL\",\"url\":\"www.5tps.com/down/22322_49_1_1.html\",\"isNewTabForeground\":true}
*** sendlink page://yunbrowser.yunos.com/browser -d {\"action\":\"LOAD_URL\",\"url\":\"www.m117.com/down-wuqu-1-66-1.html\",\"isNewTabForeground\":true}
*** ./mk_yunos.sh aplk_nuc user cts --enable-cntr-hal=no --enable-cntr-cvg=no --with-container=no --enable-cntr-rt=no --with-toolchainname=i686-linux-gnu --enable-unified-surface=yes --enable-closed-source=no
** CTS commands
*** run cts -m CtsProviderTestCases -t android.provider.cts.Settings_SystemTest#testSystemSettings
*** run cts -m CtsProviderTestCases -t android.provider.cts.SettingsTest#testSystemTable
