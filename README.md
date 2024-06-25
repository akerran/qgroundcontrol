# Technical task implementation summary

Added ability to stream video from two new sources:
* local video file
* web location

# Some implementation details:
* src/VideoReceiver/GstVideoReceiver.cc - the main functionality implemented in this file, where were added new gstreamer source elements for local file (filesrc) and for web location (souphttpsrc). New sources were imported into existing flow, so that existing pipeline schema with both gstreamer decoder and recorder queues are left unaffected.
* src/UI/preferences/VideoSettings.qml - new UI elements in Video menu to handle connection strings for new sources
* libs/mavlink/include/mavlink/v2.0/common/common.h - changes in this submodule were added in order to support new types of video sources, therefore updated enum VIDEO_STREAM_TYPE with new members:
  * VIDEO_STREAM_TYPE_LOCAL=4, /* Stream local video file (URI gives the file path) | */
  * VIDEO_STREAM_TYPE_WEB=5, /* Stream is web video file (URI gives the URL of video file) | */

# Installation and running prerequisites
This fork of qgroundcontrol software has the same requirements as original one:
gstreamer libraries and Qt6.6.3 installed
 

In order to stream local file:
Application settings --> Video --> Video source: Choose "Local File Stream" option from drop box
enter full path for video file to be streamed, e.g. /home/username/Videos/video.mpg
Turn off "Low latency" option


Stream video from web location:
Application settings --> Video --> Video source: Choose "Web Location Stream" option from drop box
enter full path for video file to be streamed, e.g. 
Turn on "Low latency" option
