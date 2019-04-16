void adjust();
int main()
{
//remember: roomba is backwards (all drive codes = backwards)
  int bucket = 3;
  //int reel = 3; (used in other functions; here for reference)
  //int bar = 2; (used in other functions; here for reference)
  int lineFollow = 0; //sensor
  int stop = 1; //sensor
  //int burning = 2;
  //wait_for_light(#)
  shut_down_in(118);
  create_connect();
  enable_servos();
  set_servo_position(bucket, 500);
  
  create_drive_direct(100, 100);//move out of box
    msleep(5500);
  create_drive_direct (200, -200);//turn 90
  	msleep (900);
  create_drive_direct(-200, -200);//move beyond box line
  	msleep (1000);
  while (analog(lineFollow) < 2000){ //move until hit gray line
create_drive_direct(-200, -200);
  }
    create_drive_direct(30, 30);//move off tape
    	msleep(800);
    
    adjust(); //tries to put both on line
	create_drive_direct(10, 10);
		msleep (1000);
	while (analog(0)<1700 && analog(stop)<1700){ //checks if both are level
     	create_drive_direct(-10, -10);
		}
	if (analog(0)>800 && analog(1)>800){
     create_drive_direct(0, 0);
	}
	else {
	adjust();
		}
    
    create_drive_direct(-80, -80);//moves into blue area
    	msleep(4000);
    create_drive_direct(-50, 50);
    	msleep(2200);
  	create_drive_direct(-50, -50);
    	msleep(4000);
    create_drive_direct(0,0);
    	msleep(1000);

lineFollowStop();//line follow until horizontal blue

    create_drive_direct(60, 60);//moves away to set up arm
    	msleep(4000);
    create_stop();
    
    readyCzechs();
    
  	create_drive_direct(-60,-60);//move to people
    	msleep(4000);
    create_drive_direct(0,0);
    defenestrate();
  create_disconnect();
  disable_servos();
  ao();
    return 0;
}
void adjust(){
while (analog(0) < 1900){
     create_drive_direct(-10, -10);
}
while (analog(1) < 1600){
     create_drive_direct(-20, -10);
}
}
void lineFollowStop(){
    while (analog(0) < 1950){
        if (analog(1) < 1600){
            create_drive_direct(-50, -10);
            	msleep(700);
        }
        else {
            create_drive_direct(-10, -50);
            	msleep(700);
        }
    }
}

