#!/usr/bin/env python
# coding: utf-8

# In[1]:


import time
import ipywidgets as widgets
from IPython.display import display
from Arm_Lib import Arm_Device

# Initialize the DOFBOT Arm
Arm = Arm_Device()
time.sleep(0.1)

# Default Home joint positions (in degrees)
HOME_POSITIONS = [90,90,90,90,90,90]

# Initial setup: move to home position
Arm.Arm_serial_servo_write6(*HOME_POSITIONS, 1000)
time.sleep(1)

# --- Define UI Controls ---

# Sliders for Joint 1 to Joint 6
# Servo limits: Joints 1-4 (0 to 180), Joint 5 (0 to 270/180 depending on model, standard is 0-180 for standard motion), Joint 6 (0 to 180 for gripper)
sliders = []
joint_names = [
    "Joint 1 (Base)",
    "Joint 2 (Shoulder)",
    "Joint 3 (Elbow)",
    "Joint 4 (Wrist Pitch)",
    "Joint 5 (Wrist Roll)",
    "Joint 6 (Gripper)"
]

for i, name in enumerate(joint_names):
    slider = widgets.IntSlider(
        value=HOME_POSITIONS[i],
        min=0,
        max=180,
        step=1,
        description=f"J{i+1}:",
        continuous_update=False,  # Sends command only when slider handle is released
        style={'description_width': 'initial'},
        layout=widgets.Layout(width='400px')
    )
    sliders.append(slider)

# Output area for logging position outputs
output = widgets.Output()

# --- Callback Functions ---

def update_joint(change, joint_id):
    """Callback triggered when a slider value changes."""
    angle = change['new']
    # Arm_serial_servo_write(servo_id, angle, time_ms)
    Arm.Arm_serial_servo_write(joint_id + 1, angle, 500)

# Attach callback to sliders
for i, slider in enumerate(sliders):
    slider.observe(lambda change, idx=i: update_joint(change, idx), names='value')

def on_print_click(b):
    """Prints current joint positions to the output widget."""
    with output:
        output.clear_output()
        current_angles = []
        for i in range(1, 7):
            angle = Arm.Arm_serial_servo_read(i)
            current_angles.append(angle)
            time.sleep(0.01)
        print(f"Current Joint Positions (J1 - J6): {current_angles}")

def on_reset_click(b):
    """Resets all joints back to home position."""
    # Send hardware command to move back home smoothly
    Arm.Arm_serial_servo_write6(*HOME_POSITIONS, 1000)
    time.sleep(1)
    
    # Update slider UI without re-triggering callbacks simultaneously
    for i, slider in enumerate(sliders):
        slider.value = HOME_POSITIONS[i]
        
    with output:
        output.clear_output()
        print("Arm reset to Home position (90°, 90°, 90°, 90°, 90°, 90°)")

# --- Buttons ---

btn_print = widgets.Button(
    description="Print Joint Pos",
    button_style="info",
    icon="print",
    layout=widgets.Layout(width='195px')
)
btn_print.on_click(on_print_click)

btn_reset = widgets.Button(
    description="Reset Home",
    button_style="warning",
    icon="home",
    layout=widgets.Layout(width='195px')
)
btn_reset.on_click(on_reset_click)

# --- Display Layout ---

button_box = widgets.HBox([btn_print, btn_reset])
ui_layout = widgets.VBox([
    widgets.HTML("<h3>DOFBOT Arm Joint Control</h3>"),
    *sliders,
    button_box,
    output
])

display(ui_layout)


# In[2]:


import Arm_Lib
Arm = Arm_Lib.Arm_Device()
joints_0 = [90, 135, 0, 0, 90, 10]
Arm.Arm_serial_servo_write6_array(joints_0, 1000)


# In[16]:


import time
import Arm_Lib
Arm = Arm_Lib.Arm_Device()
Arm.Arm_serial_servo_write(1,60,100)
time.sleep(0.5)
Arm.Arm_serial_servo_write(2,80,100)
time.sleep(0.5)
Arm.Arm_serial_servo_write(3,80,100)
time.sleep(0.5)
Arm.Arm_serial_servo_write(4,180,100)
time.sleep(0.5)
Arm.Arm_serial_servo_write(5,80,100)
time.sleep(0.5)
Arm.Arm_serial_servo_write(6,80,100)
time.sleep(0.5)


# In[65]:


import Arm_Lib
Arm=Arm_Lib.Arm_Device()
harini=[31,92,21,18,24,20]
Arm.Arm_serial_servo_write6_array(harini,1000)


# In[25]:


import Arm_Lib
Arm=Arm_Lib.Arm_Device()
Arm.Arm_serial_servo_write6(120,130,140,160,170,180,500)


# In[38]:


import Arm_Lib
Arm=Arm_Lib.Arm_Device()
Arm.Arm_serial_servo_write6(80,90,120,100,160,110,1000)


# In[39]:


import Arm_Lib
Arm=Arm_Lib.Arm_Device()
Arm.Arm_serial_servo_write6(70,80,110,130,150,100,1000)


# In[62]:


import Arm_Lib
Arm=Arm_Lib.Arm_Device()
Arm.Arm_serial_servo_write6(60,70,100,110,120,130,1000)


# In[60]:


import Arm_Lib
Arm=Arm_Lib.Arm_Device()
Arm.Arm_serial_servo_write6(50,60,70,80,100,110,1000)


# In[2]:


import Arm_Lib
Arm=Arm_Lib.Arm_Device()
Arm.Arm_serial_servo_write6(127,40,68,90,90,118,1000)
time.sleep(0.5)


# In[ ]:




