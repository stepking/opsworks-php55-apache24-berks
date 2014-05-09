# Opsworks Berkshelf file
#
#
source "https://api.berkshelf.com"
metadata

# Include Local Opsworks Cookbooks
opsworks_cb_path = '/opt/aws/opsworks/current/cookbooks'
opsworks_cookbooks = Dir[opsworks_cb_path + '/*'].select { |f| File.directory?(f) }.map { |f| File.basename(f) }

# Don't install these cookbooks with berkshelf
opwsorks_exclude = ['deploy','apache2','mod_php5_apache2','dependencies']

# Get all of the opworks cookbooks
opsworks_cookbooks.each do |cb|
cookbook(cb, path: File.join(opsworks_cb_path, cb))
end

#overidden cookbooks
cookbook "apache2", git: "https://github.com/onehealth-cookbooks/apache2.git"
cookbook "mod_php5_apache2", git: "https://github.com/stepking/opsworks-php55-apache24.git", rel: "mod_php5_apache2"
cookbook "dependencies", git: "https://github.com/stepking/opsworks-cookbooks.git", rel:"dependencies", branch: "release-chef-11.10"
cookbook "deploy", git: "https://github.com/stepking/opsworks-cookbooks.git", rel:"deploy", branch: "release-chef-11.10"
