void moveForward();\
void moveBackward();\
void turnRight();\
void turnLeft();\
int main(){\
  //wait_for_light();\
  shut_down_in(118);\
  enable_servos();\
  
  disable_servos();\
  ao();\
  return 0;\
}\
void moveForward(){
mav (0, 1000);
mav (1, 1000);
}\
void moveBackward(){
mav (0, -800);
mav (1, -800);
}\
void turnRight(){
  mav(0, -500);
  mav(1, 500);
  msleep(2000);
}\
void turnLeft(){
  mav(0, 500);
  mav(1, -500);
  msleep(2000);
}
