node {
   println 'Installer for Puppet Server'
   sh 'rm -rf *'
   stage("Clone Git Repo") {
       checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'install-dir']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/moziauddin/puppet-install.git']]])
   }
   stage("Installatiion") {
       dir("install-dir") {
           sh 'pwd && whoami && ls -lahF'
           sh 'ansible-playbook playbooks/install-puppet.yml -i inventory/main.yml -v'
   }
 }
}
