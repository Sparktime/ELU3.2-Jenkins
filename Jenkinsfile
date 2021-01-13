pipeline {
    agent any

    stages {
        
                stage('Katalon') {
             steps {
             executeKatalon executeArgs: 'katalonc -noSplash -runMode=console -projectPath="C:\\School\\webshop-Concept\\My First Web UI Project.prj" -retry=0 -testSuitePath="Test Suites/Test" -executionProfile="default" -browserType="Chrome" -apiKey="05f12e26-63d2-4b49-8694-28431f56fa4d"  -reportFolder="C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Pipeline\\Katalon\\Reports" -reportFileName="report" --config -proxy.auth.option=NO_PROXY -proxy.system.option=NO_PROXY -proxy.system.applyToDesiredCapabilities=true', location: 'C:\\School\\Katalon_Studio_Engine_Windows_64-7.8.1\\', version: '', x11Display: '', xvfbConfiguration: ''
             publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, includes: '**/*', keepAll: false, reportDir: 'Katalon\\Reports', reportFiles: 'report.html', reportName: 'Katalon Report', reportTitles: ''])
                    }
        }
        
        stage('dotcover') {
            steps {
                bat 'C:\\School\\JetBrains.dotCover.CommandLineTools.2020.3\\dotcover.exe cover --TargetExecutable="C:\\School\\NUnit.Console-3.12.0-beta1\\bin\\netcoreapp3.1\\nunit3-console.exe" --TargetArguments="C:\\School\\elu3.2\\stap01\\DetermineShippingCostsTest\\bin\\Debug\\netcoreapp3.1\\DetermineShippingCostsTest.dll" --Output="coverageReport\\dotcoverreport.html" --ReportType="HTML"'
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, includes: '**/*', keepAll: false, reportDir: 'coverageReport', reportFiles: 'dotcoverreport.html', reportName: 'Dotcover Report', reportTitles: ''])            
                }
        }
        stage('Unittest') {
            steps {
                bat 'C:\\School\\NUnit.Console-3.12.0-beta1\\bin\\netcoreapp3.1\\nunit3-console.exe C:\\School\\elu3.2\\stap01\\DetermineShippingCostsTest\\bin\\Debug\\netcoreapp3.1\\DetermineShippingCostsTest.dll'
                nunit testResultsPattern: 'TestResult.xml'
                
         }
         }
         
                 stage('SoapUI') {
            steps {
                bat 'C:\\School\\SoapUI-5.6.0\\bin\\testrunner.bat -sSoapUI -a -j -J -fC:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Pipeline\\SoapUI "C:\\School\\SoapUIxml\\Soapui-project.xml"'
                junit 'SoapUI\\TEST-SoapUI.xml'
                
            }
        }
         
                  stage('Neoload') {
            steps {
                bat '"C:\\Program Files\\NeoLoad 7.7\\bin\\NeoLoadCmd.exe" -noGUI -project="C:\\School\\NeoLoad\\NeoloadV2\\NeoloadV2.nlp" "C:\\School\\NeoLoad\\NeoloadV2\\sla_profiles\\soapcall.xml"  -launch="scenario1" -report "C:\\Windows\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins\\.jenkins\\workspace\\Pipeline\\NeoLoad\\report.xml"'
				publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, includes: '**/*', keepAll: false, reportDir: 'Neoload', reportFiles: 'report.html', reportName: 'NeoLoad Report', reportTitles: ''])  

         }
         }
         

    
    }
}
