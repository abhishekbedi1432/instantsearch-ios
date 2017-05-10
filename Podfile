# Uncomment the next line to define a global platform for your project
# platform :ios, '9.0'

use_frameworks!

def instantsearch_core
    pod "InstantSearch-Core-Swift", :path => '/Users/guydaher/Developer/Algolia/iOS/instantsearch-core-swift'
end

target 'InstantSearch' do
  instantsearch_core
  pod 'SwiftLint'
  
  target 'InstantSearchTests' do
      inherit! :search_paths
  end
  
  target 'Example' do
      workspace 'InstantSearch.xcworkspace'
      project 'Example/Example.xcodeproj'
      instantsearch_core
  end
end


post_install do |installer|
    installer.pods_project.targets.each do |target|
        # add this line
        target.new_shell_script_build_phase.shell_script = "mkdir -p $PODS_CONFIGURATION_BUILD_DIR/#{target.name}"
        target.build_configurations.each do |config|
            config.build_settings['CONFIGURATION_BUILD_DIR'] = '$PODS_CONFIGURATION_BUILD_DIR'
        end
    end
end
