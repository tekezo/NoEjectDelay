#CONFIGURATION = Debug
CONFIGURATION = Release

AUTOUPDATE_ICON = 'build/Release/NoEjectDelay Utility.app/Contents/Frameworks/Sparkle.framework/Versions/A/Resources/Autoupdate.app/Contents/Resources/AppIcon.icns'

all:
	$(MAKE) -C ../../../pkginfo
	(cd Pods && xcodebuild -configuration $(CONFIGURATION) SYMROOT=$(CURDIR)/build)
	xcodebuild -alltargets -configuration $(CONFIGURATION) build
	[ -f $(AUTOUPDATE_ICON) ] || exit 1
	install -m 644 ../../share/Resources/app.icns $(AUTOUPDATE_ICON)

clean:
	rm -rf build
	rm -f Info.plist
	rm -f *.xcodeproj/*.mode1
	rm -f *.xcodeproj/*.mode1v3
	rm -f *.xcodeproj/*.pbxuser
	rm -rf *.xcodeproj/xcuserdata
	rm -rf *.xcodeproj/project.xcworkspace/xcuserdata

xcode:
	open *.xcworkspace

run: all
	open 'build/Release/NoEjectDelay Utility.app'

podupdate:
	pod update
	pod install --no-repo-update
