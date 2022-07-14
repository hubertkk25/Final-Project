# Final-Project



network topology 



![image](https://user-images.githubusercontent.com/96326971/178898808-d6d8a057-6f76-45f6-a570-732669d6a6c0.png)




vunerabilties on target 1: Weak passwords
                           surver vulnerable to wpscan
                           wordpress config has invalid permission
                           
alerts implemented : when 400 or more login failures happen in 5 minute period.
                          400 login failures in a 5 min period
                          
                          
                          
                          
                          
                          
![image](https://user-images.githubusercontent.com/96326971/178899549-aa17c896-48c1-4ad7-8c5a-88d08c06de8a.png)




cpu monitor summarize the following: Which metric does this alert monitor?This monitors CPU usage on the Target 1 Server
                                     What is the threshold it fires at?50% CPU usage






![image](https://user-images.githubusercontent.com/96326971/178900000-ed46e7cf-2bfe-48ce-8351-46f9d8568e0f.png)







hardening:   
Explain how to patch Target 1 against Vulnerability 1.           
To address weak passwords, force a password policy that requires the use of strong passwords and password reset policy.


![image](https://user-images.githubusercontent.com/96326971/178900180-249726d1-346c-401c-8a0b-e96acf09af17.png)



Explain how to patch Target 1 against Vulnerability 2. Include:
Change the permissions of the wordpress directory to prevent unauthorized access to the wordpress config files.
chmod 700 /var/www/html/wordpress/*
![image](https://user-images.githubusercontent.com/96326971/178900393-408e604d-83af-43b6-8e91-74d920e5b82c.png)



Explain how to patch Target 1 against Vulnerability 3. Include:
Require strong passwords at the database level for authentication.
![image](https://user-images.githubusercontent.com/96326971/178900481-1e04d7ac-3f3b-463b-be03-2ffa1c57d572.png)

        

              
Explain how to patch Target 2 against Vulnerability 1. Include: 
Either upgrade to the latest version of wordpress, or use a more secure content management system.



![image](https://user-images.githubusercontent.com/96326971/178900534-4a30f7be-a72b-4240-b99c-20f74501cd57.png)





implementing patches:


Ansible could be used to update Word Press, Apache and the OS.  
An example ansible playbook task to update the WP Core system could look like:

- name: Update WordPress Core (Major version)
  command: "{{ wpclipath }} core update"
  when: major is defined
  args:
    chdir: '{{ projects[inventory_hostname].blog_folder }}'!
    
    
    
    [image](https://user-images.githubusercontent.com/96326971/178900577-68c20717-c325-4c55-b0d1-3c1b83440acf.png)



An example ansible playbook task to update Ububtu and all packages could look like:

- name: Update apt-get repo and cache
  apt: update_cache=yes force_apt_get=yes cache_valid_time=3600




![image](https://user-images.githubusercontent.com/96326971/178900739-20f3cd4f-5f88-4f10-8894-405e886c631b.png)
