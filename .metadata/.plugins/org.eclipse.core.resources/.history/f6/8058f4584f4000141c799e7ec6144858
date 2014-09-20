import java.net.InetSocketAddress;
import java.util.concurrent.Executors;
import org.jboss.netty.bootstrap.ServerBootstrap;
import org.jboss.netty.buffer.ChannelBuffer;
import org.jboss.netty.channel.Channel;
import org.jboss.netty.channel.ChannelEvent;
import org.jboss.netty.channel.ChannelFactory;
import org.jboss.netty.channel.ChannelHandlerContext;
import org.jboss.netty.channel.ChannelPipeline;
import org.jboss.netty.channel.ChannelPipelineFactory;
import org.jboss.netty.channel.ChannelStateEvent;
import org.jboss.netty.channel.Channels;
import org.jboss.netty.channel.ExceptionEvent;
import org.jboss.netty.channel.MessageEvent;
import org.jboss.netty.channel.SimpleChannelHandler;
import org.jboss.netty.channel.SimpleChannelUpstreamHandler;
import org.jboss.netty.channel.socket.nio.NioServerSocketChannelFactory;

public class echoServer {
	public static class EchoServerHandler extends SimpleChannelUpstreamHandler {

		 @Override
	     public void handleUpstream(ChannelHandlerContext ctx, ChannelEvent e) throws Exception {

	         // Log all channel state changes.
	         if (e instanceof ChannelStateEvent) {
	        	 System.out.println("Channel state changed: " + e);
	         }

	         super.handleUpstream(ctx, e);

	     }

		@Override
		public void messageReceived(ChannelHandlerContext ctx, MessageEvent e) {
			//Use channel buffer to get the message from MessageEvent e and copy each character read to a string
//check for occurence of '\n' or '\r' characters and if yes then print the above string 
			ChannelBuffer buf = (ChannelBuffer) e.getMessage();
		    while(buf.readable()) {
		        System.out.println((char) buf.readByte());
		        System.out.flush();
		    }
		}

		@Override
		public void channelOpen(ChannelHandlerContext ctx, ChannelStateEvent e)
				throws Exception {

		}

		@Override
		public void exceptionCaught(ChannelHandlerContext ctx, ExceptionEvent e) {
			e.getCause().printStackTrace();
			System.out.println(e.toString());
			Channel ch = e.getChannel();
			ch.close();
		}
	}

	public static class NettyServer {

		public void startServer() throws Exception {
			ChannelFactory factory = new NioServerSocketChannelFactory(
					Executors.newCachedThreadPool(),
					Executors.newCachedThreadPool());
//Create and instance of server bootstrap and bind it to InetSocketAddress
		}
	}

	public static void main(String[] args) throws Exception {
		// TODO Auto-generated method stub
		NettyServer ns = new NettyServer();
		ns.startServer();

	}
}