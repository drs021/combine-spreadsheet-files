# combine-spreadsheet-files

# This is a simple script to compile multiple csv's into a single excel sheet. 

import pandas as pd
#import os
import glob


folder_path = r"FILE_NAME_HERE"  # Replace with your actual folder path

# get data file names
filenames = glob.glob(folder_path + "/*.csv")

dfs = []
for filename in filenames:
    dfs.append(pd.read_csv(filename))
    
    
# Concatenate all data into one DataFrame
big_frame = pd.concat(dfs, ignore_index=True)

big_frame.to_excel('combined sheets.xlsx')
print(big_frame.head())
