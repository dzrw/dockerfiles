- Let's make some kind of command-line minecraft package manager that makes downloading mod versions not a complete shitshow.
	- it should download an index, and then use that to download the mods from their origins
	- no need to host the files ourselves.

	

# so, maybe it's NEI that's broken.
RUN rm /opt/minecraft/mods/NotEnoughItems-1.7.10-1.0.4.107-universal.jar \
 && curl -jkSL -o /opt/minecraft/mods/NotEnoughItems-1.7.10-1.0.5.111-universal.jar "http://chickenbones.net/maven/codechicken/NotEnoughItems/1.7.10-1.0.5.111/NotEnoughItems-1.7.10-1.0.5.111-universal.jar" \
 && rm /opt/minecraft/mods/CodeChickenCore-1.7.10-1.0.6.43-universal.jar \
 && curl -jkSL -o /opt/minecraft/mods/CodeChickenCore-1.7.10-1.0.7.46-universal.jar "http://chickenbones.net/maven/codechicken/CodeChickenCore/1.7.10-1.0.7.46/CodeChickenCore-1.7.10-1.0.7.46-universal.jar"
