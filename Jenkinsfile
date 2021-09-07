def gv

pipeline
agent any  
{
	parameters
	{
		choice(name: 'Version', choices: ['1.1', '2.1', '2.9'], description: '')
		booleanParam(name: 'executeTests', defaultValue: true , description: '')
	}
	stages
	{
		stage ("Init")
		{
			steps
			{
				script
				{
					gv= load "script.groovy"
				}
			}
		}

		stage ("Build")
		{
			steps
			{
				script
				{
					gv.buildApp()
				}

			}
		}

		stage ("Test")
		{
			when
			{
				expression
				{
					params.executeTests()
				}

			}
			steps
			{
				script
				{
					gv.testApp()
				}

			}
		}

		stage ("Deploy")
		{
			steps
			{
				script
				{
					gv.deployApp()
				}
			}
		}
	}
}
