The purpose of renameFilesByDate.py, is to get the taken date of a photo.
and to rename the photo with that timestamp:
20160722_173949_52126.jpg YEARMONTHDAY_HOURMINSEC_RANDOM.EXT
The best source from where to get this, is from date_taken metadata.
But older photos and the WHATSAPP ones, do not have this metadata
So we will establish the date from the following sources (in this order):
1) From date_taken medatada
2) If date_taken not present, will try media_created (as well metadata, but for videos)
3) If none present, we will try to get if from name
4) Lastly, From last modified. This is not safe, because for example if you rotate
      a photo, last modified date will be updated

Use:
Set startDir from file with the directory where you want to apply
python3 renameFilesByDate.py


Flow when want to add new pictures / videos to existing collection:

1) Delete all .AAE files
2) Run dupeGuru, in "Content" way to delete all 100% identicals
3) Run dupeGuru, in "Pictures" way, with index 96% to delete duplicate pictures
     (96% is good to detect similar between Whatsapp and Camera)
4) Run VideoDuplicateFinder, with index 99% to delete Video duplicates (.MOV files form Iphone)
5) Run renameFilesByDate.py to rename the pictures/videos.
6) Merge pictures
