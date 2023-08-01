# NerdNet
MERN FULLSTACK APP


This MERN Social Media App is a full-featured social media application that includes user authentication, profile management, post creation, likes, comments, and a real-time chat system. This project demonstrates the ability to create a complex, full-stack application using modern web development technologies.


Clone the repository: 
git clone https://github.com/abuka2323/mern-social-media.git 


 ---> cd server --> npm install
// dataFetcher.test.js (or any appropriate test file)
import DataFetcher from './dataFetcher'; // Import the DataFetcher class
import { jest } from '@jest/globals'; // Import Jest's mocking capabilities

describe('DataFetcher', () => {
  // Mock the Falcor model
  const mockModel = {
    getValue: jest.fn(),
  };

  // Create a new instance of DataFetcher with the mocked model
  const dataFetcher = new DataFetcher(mockModel);

  // Test positive scenario
  it('should fetch page JSON from MCM API', async () => {
    const nodeId = 'someNodeId';
    const expectedResponse = { someKey: 'someValue' };
    mockModel.getValue.mockResolvedValue(expectedResponse);

    const result = await dataFetcher.fetchPageJson(nodeId);

    expect(result).toEqual(expectedResponse);
    expect(mockModel.getValue).toHaveBeenCalledWith(
      `mcm.versionedison.vl.versionedJsonIds["${nodeId}"].json`
    );
  });

  // Test error scenario
  it('should throw an error when API call fails', async () => {
    const nodeId = 'invalidNodeId';
    const expectedError = new Error('Failed to get page JSON. Error from Falcor:');
    mockModel.getValue.mockRejectedValue(expectedError);

    await expect(dataFetcher.fetchPageJson(nodeId)).rejects.toThrow(expectedError);
    expect(mockModel.getValue).toHaveBeenCalledWith(
      `mcm.versionedison.vl.versionedJsonIds["${nodeId}"].json`
    );
  });
});
 
 ---> cd client --> npm install

 to run locally --> npm start 
 
