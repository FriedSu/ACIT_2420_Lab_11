# ACIT_2420_Lab_11

Files that are included in this package:
	 wthr_srvc
	 wthr_srvc.service
	 wthr_srvc.timer

	1. (wthr_srvc)

		a. Move wthr_srvc to an appropriate file location, this will be a fixed location, and you cannot change the location as the service will not work if the script is not in the same path

You may also use a custom path, but you will have to edit the service file and give the same file location as where the script file is.
*(if you want more information about custom file location for the script and editting the service file, please see the bottom of this instruction guide.)*

			i. The file location that you must have in order for the service to work with the script is the following file location: ~/documents/Labs/lab_11/ACIT_2420_Lab_11

			ii. After moving the wthr_srvc script into the file location, to give the user permission to execute the script, run this command: chmod +x wthr_srvc


	2. (wthr_srvc.service)

		a. The wthr_srvc.service file must be in the following file location to function: /etc/systemd/system


	3. (wthr_srvc.timer)

		a. The wthr_srvc.timer file will also be in the same file location as the wthr_srvc.service file: /etc/systemd/system


After you have moved all the files to their appropriate places, run this command: sudo systemctl daemon-reload
	
The final step to finally make the service functional is this last command: sudo systemctl start wthr_srvc.timer 
	
That command will activate the wthr_srvc.timer file which triggers the wthr_srvc.service file that runs the wthr_srvc script.
	
The script is now fully functioning on your system!

-----------------------------------------------------------------------------------------------------------------------------

If you want to use a custom location for your wthr_srvc script please read below:

For example: You moved the wthr_srvc script to the following path (assuming the directory exists): /home/vagrant/documents/Example_Folder 

	1. Navigate to your wthr_srvc.service once you have the file moved to the following path: ~/etc/systemd/system

	2. While you are in the path ~/etc/systemd/system, Use the following command to edit the service file: sudo vim wthr_srvc.service

		a. In the service file, look for the following:

			ExecStart=/home/vagrant/documents/Labs/lab_11/wthr_srvc
			
			WorkingDirectory=/home/vagrant/documents/Labs/lab_11
			
		b. With the original given example (/home/vagrant/documents/Example_Folder) the new paths should look like this

			ExecStart=/home/vagrant/documents/Example_Folder/wthr_srvc
			
			WorkingDirectory=/home/vagrant/documents/Example_Folder

		The ExecStart will include the wthr_srvc script in the path.
		The WorkingDirectory will not include the wthr_srvc scipt in the path

You are all done configuring your service file to work in another file location!

