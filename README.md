# pytorch0724
<br><br>
### dataset 구성

---------
<br>


<table>

  <tr>
    <td></td>
    <td></td>
  </tr>
  
  <tr>
    <td>
    ~~~python
      # x_data 초기화
x_data = []


'''    x_data,       y_data '''
'''(1000,4,257,382), (1000,)'''


for idx in range(1000):

    # list 초기화
    x_element = []


    """ Mag """
    # S_left,  S_right 의 idx번째 array
    x_L = S_L_mag[:,:,idx]
    x_R = S_R_mag[:,:,idx]



    """log scale [dB]"""
    x_L_dB = 20*np.log10( np.abs(x_L) + np.finfo(np.float32).eps )
    x_R_dB = 20*np.log10( np.abs(x_R) + np.finfo(np.float32).eps )
    #x_L = librosa.amplitude_to_db(x_L)
    #x_R = librosa.amplitude_to_db(x_R)



    """phase"""
    # S_left_phase,  S_right_phase 의 idx번째 array
    x_L_phase =  S_L_phase[:,:,idx] 
    x_R_phase =  S_R_phase[:,:,idx] 

    


    """normalization"""
    x_L, x_R = Mag_normalization(x_L_dB, x_R_dB)
    x_L_phase = Phase_normalization( x_L_phase )
    x_R_phase = Phase_normalization( x_R_phase )




    """x_element.shape ==> (4, 257, 382)"""
    # 초기화된 list( x_element )에 
    # left, right의 mag[dB], phase[rad] 총 4개의 array 삽입 
    x_element.append(x_L)
    x_element.append(x_R)
    x_element.append(x_L_phase)
    x_element.append(x_R_phase)



    # x_element 의 type을 list에서 numpy array로 변환후 
    #x_data list에 삽입
    x_data.append( np.asarray(x_element) )



# x_data의 type을 list에서 numpy array로 변환
x_data = np.asarray(x_data)

# 0,20,40,60...180,-1 인 y_data를  Y_DATA 함수로 
# 0,1,2,....,9,10 으로 변환
y_data = Y_DATA( y )


print('x_data:', x_data.shape)
print('y_data:', y_data.shape)
      ~~~~
    </td>
    
   <td>
    ~~~python
      # x_data 초기화
x_data = []


'''    x_data,       y_data '''
'''(1000,4,257,382), (1000,)'''


for idx in range(1000):

    # list 초기화
    x_element = []


    """ Mag """
    # S_left,  S_right 의 idx번째 array
    x_L = S_L_mag[:,:,idx]
    x_R = S_R_mag[:,:,idx]



    """log scale [dB]"""
    x_L_dB = 20*np.log10( np.abs(x_L) + np.finfo(np.float32).eps )
    x_R_dB = 20*np.log10( np.abs(x_R) + np.finfo(np.float32).eps )
    #x_L = librosa.amplitude_to_db(x_L)
    #x_R = librosa.amplitude_to_db(x_R)



    """phase"""
    # S_left_phase,  S_right_phase 의 idx번째 array
    x_L_phase =  S_L_phase[:,:,idx] 
    x_R_phase =  S_R_phase[:,:,idx] 

    


    """normalization"""
    x_L, x_R = Mag_normalization(x_L_dB, x_R_dB)
    x_L_phase = Phase_normalization( x_L_phase )
    x_R_phase = Phase_normalization( x_R_phase )




    """x_element.shape ==> (4, 257, 382)"""
    # 초기화된 list( x_element )에 
    # left, right의 mag[dB], phase[rad] 총 4개의 array 삽입 
    x_element.append(x_L)
    x_element.append(x_R)
    x_element.append(x_L_phase)
    x_element.append(x_R_phase)



    # x_element 의 type을 list에서 numpy array로 변환후 
    #x_data list에 삽입
    x_data.append( np.asarray(x_element) )



# x_data의 type을 list에서 numpy array로 변환
x_data = np.asarray(x_data)

# 0,20,40,60...180,-1 인 y_data를  Y_DATA 함수로 
# 0,1,2,....,9,10 으로 변환
y_data = Y_DATA( y )


print('x_data:', x_data.shape)
print('y_data:', y_data.shape)
      ~~~
    </td>

</table>

