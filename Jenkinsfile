#!/usr/bin/groovy
@Library('github.com/hrishin/osio-pipeline@iss#43-build-event')_
osio {
    config runtime: 'node'

    ci {
        def app = processTemplate(
          params: [ release_version: "1.0.${env.BUILD_NUMBER}" ]
        )
        build resources: app
    }

    cd {
        def app = processTemplate(
          params: [ release_version: "1.0.${env.BUILD_NUMBER}" ]
        )
        build resources: app
        def service = loadResources(file: './.openshiftio/service.yaml')
        deploy resources: [app, service], env: 'stage'
    }
}
