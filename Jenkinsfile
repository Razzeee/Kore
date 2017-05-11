
node {
 currentBuild.displayName = ${ENV,var="GITHUB_REPO"}-${ENV,var="Revision"}-${GIT_REVISION,length=7}

 stage 'checkout'
  checkout scm

 stage 'build'
  try {
   sh '. $WORKSPACE/tools/jenkins/buildsteps/build-release'
   sh 'export RUN_SIGNSTEP="$WORKSPACE/../../android-dev/signing/doreleasesign.sh"
. $WORKSPACE/tools/jenkins/buildsteps/package'
  } catch(err) {
   currentBuild.result = FAILURE
  }
  
 stage 'upload'

     
}
